<template>
    <div id=containerFetch>
        <button id="ozae">Ozae</button>
        <button id="users">Users</button>
        <button id="posts">Posts</button>
    </div>
</template>
<script>
    export default {
        name: 'TestFetchAPI'
    }

    var secretKey = '474d3500db4940e2945a33eb7788710d';
    var objectCountries = [
        {
            id:     "fr-fr",
            name:   "France"
        },
        {
            id:     "en-us-ny",
            name:   "États-Unis (New York)"
        },
        {
            id:     "en-us-df",
            name:   "États-Unis (San Francisco)"
        },
        {
            id:     "en-gb",
            name:   "Royaume-Uni"
        },
        {
            id:     "fr-be",
            name:   "Belgique (Français)"
        },
        {
            id:     "nl-be",
            name:   "Belgique (Néerlandais)"
        },
        {
            id:     "de-de",
            name:   "Allemagne"
        }
    ];
    var objectCategories = [
        {
            id:     "w",
            name:   "International"
        },
        {
            id:     "n",
            name:   "National"
        },
        {
            id:     "b",
            name:   "Économie"
        },
        {
            id:     "t",
            name:   "Science / Tech"
        },
        {
            id:     "e",
            name:   "Divertissement"
        },
        {
            id:     "s",
            name:   "Sports"
        },
        {
            id:     "m",
            name:   "Santé"
        },
        {
            id:     "_",
            name:   "À la une"
        }
    ]

    console.log(objectCountries, objectCategories);

    document.addEventListener('click', async (event) =>
    {
        if (event.target.matches('#ozae'))
        {
            try
            {
                const url = "https://api.ozae.com/gnw/articles?date=20180701__20180702&edition=fr-fr&key=" + secretKey + "&hard_limit=50";
                const response = await fetch(url);

                if (response.ok)
                {
                    let data = await response.json();
                    const fragment = document.createDocumentFragment();

                    for (let i = 0; i < data['articles'].length; i++)
                    {
                        const div = document.createElement('div');
                        div.innerHTML = data['articles'][i]['name'];
                        fragment.appendChild(div);
                    }

                    document.getElementById('containerFetch').appendChild(fragment);
                    console.log(data);
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
        else if (event.target.matches('#users'))
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