<template>
    <div id=containerFetch>
        <button id="users">Users</button>
        <button id="posts">Posts</button>
    </div>
</template>
<script>
    export default {
        name: 'TestFetchAPI'
    }

    document.addEventListener('click', async (event) =>
    {
        if (event.target.matches('#users'))
        {
            try
            {
                const response = await fetch('https://jsonplaceholder.typicode.com/users');

                if (response.ok)
                {
                    let data = await response.json();
                    const fragment = document.createDocumentFragment();

                    for (let i = 0; i < data.length; i++)
                    {
                        const div = document.createElement('div');
                        div.innerHTML = data[i]['name'];
                        fragment.appendChild(div);
                    }

                    document.getElementById('containerFetch').appendChild(fragment);
                }
                else
                {
                    // console.error('Retour du serveur : ', response.status);
                    const div = document.createElement('div');
                    div.innerHTML = "Retour du serveur : " + response.status;
                    document.getElementById('containerFetch').appendChild(div);
                }
            }
            catch (error)
            {
                // console.log(error);
                const div = document.createElement('div');
                div.innerHTML = error;
                document.getElementById('containerFetch').appendChild(div);
            }
        }
        else if (event.target.matches('#posts'))
        {
            try
            {
                const response = await fetch('https://jsonplaceholder.typicode.com/posts');

                if (response.ok)
                {
                    let data = await response.json();
                    const fragment = document.createDocumentFragment();

                    for (let i = 0; i < data.length; i++)
                    {
                        const div = document.createElement('div');
                        div.innerHTML = data[i]['title'];
                        fragment.appendChild(div);
                    }

                    document.getElementById('containerFetch').appendChild(fragment);
                }
                else
                {
                    // console.error('Retour du serveur : ', response.status);
                    const div = document.createElement('div');
                    div.innerHTML = "Retour du serveur : " + response.status;
                    document.getElementById('containerFetch').appendChild(div);
                }
            }
            catch (error)
            {
                // console.log(error);
                const div = document.createElement('div');
                div.innerHTML = error;
                document.getElementById('containerFetch').appendChild(div);
            }
        }
    });
</script>