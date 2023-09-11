---
layout: home
title: Pokemon Dictionary
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pokemon Search</title>
</head>
<body>
    <h1>Pokemon Search</h1>
    <label for="pokemonName">Enter Pokemon Name:</label>
    <input type="text" id="pokemonName">
    <button onclick="searchPokemon()">Search</button>
    <div id="pokemonInfo"></div>
    <script>
        const apiKey = '56cf0d9c39msh90ab47fd56c02e6p1d2792jsn0f4dfaa46b90';
        const baseUrl = 'https://pokemon-api3.p.rapidapi.com/pokemon';
        async function searchPokemon() {
            const name = document.getElementById('pokemonName').value.trim();
            if (name === '') {
                alert('Please enter a Pokemon name.');
                return;
            }
            const url = `${baseUrl}?name=${name}`;
            const options = {
                method: 'GET',
                headers: {
                    'X-RapidAPI-Key': apiKey,
                    'X-RapidAPI-Host': 'pokemon-api3.p.rapidapi.com',
                },
            };
            try {
                const response = await fetch(url, options);
                if (response.status === 200) {
                    const data = await response.json();
                    displayPokemonInfo(data);
                } else if (response.status === 404) {
                    displayMessage('Pokemon not found');
                } else {
                    throw new Error('Failed to fetch data');
                }
            } catch (error) {
                console.error(error);
                displayMessage('An error occurred');
            }
        }
        function displayPokemonInfo(pokemonData) {
            const infoDiv = document.getElementById('pokemonInfo');
            infoDiv.innerHTML = `
                <h2>${pokemonData.name}</h2>
                <img align = "left" src="${pokemonData.sprites.front_default}" alt="${pokemonData.name}">
                <p>Height: ${pokemonData.height} decimetres</p>
                <p>Weight: ${pokemonData.weight} hectograms</p>
            `;
        }
        function displayMessage(message) {
            const infoDiv = document.getElementById('pokemonInfo');
            infoDiv.innerHTML = `<p>${message}</p>`;
        }
    </script>
</body>
</html>