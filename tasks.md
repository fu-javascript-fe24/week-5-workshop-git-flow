# Tasks

## 01-createHTML
Skapa en HTML-fil och länka in filerna style.css och app.js i din Head. Namnge sidan Swapi och länka även in följande i din Head.
```<script src="https://kit.fontawesome.com/f300007e95.js" crossorigin="anonymous"></script>```

Skapa även mappen ```resources``` och lägg in bilden *header-background.png* som du hittar i repot.

## 02-createScript
Skapa en JS fil med namnet app.js. Stagea och committa. Lägg därefter in följande kod längst upp i filen
```
import apiHandler from './apiHandler.js';
import pagination from './pagination.js';
import characters from './characters.js';
```

## 03-createCSS
Skapa filen style.css och lägg in följande startstyling
```
/* BASE */
:root {
    --background-grey: #424242;
    --background-grey-light: #C4C4C4;
    --heading-grey: #535556;
    --heading-green: #748687;
    --active-grey: #444444;
    --lighter-grey: #E1DFDF;
    --darker-grey: #8E8E8E;
    --text-dark: #575859;
    --text-light: #ffffff;
    --heading-yellow: #FED702;
}

* {
    box-sizing: border-box;
    padding: 0;
    margin: 0;
}

h1, h2, h3 {
    text-transform: uppercase;
    font-family: sans-serif;
}

/* Utilities */
.content-wrapper {
    max-width: 95%;
    margin: 0 auto;
}
```

## 04-apiHandler
Skapa filen apiHandler.js och lägg in följande kod
```
async function fetchData(url) {
    try {
        const response = await fetch(url);
        const data = response.json();

        return data;
    } catch(error) {
        console.log(error);
        return [];
    }
}

export default { fetchData };
```

## 05-characters
Skapa filen characters.js och lägg in följande kod
```
const characters = [];

function getCharacters() {
    return characters;
}

function pushCharacter(character) {
    characters.push(character);
}

export default { getCharacters, pushCharacter };
```

## 06-pagination
Skapa filen pagination.js och lägg in följande kod
```
let currentPage = 1;
const itemsPerPage = 8;
let nmbrOfPosts = 0;

function getCurrentPage() {
    return currentPage;
}

function setNmbrOfPosts(nmbr) {
    nmbrOfPosts = nmbr;
}

function previousPage() {
    if(currentPage > 1) {
        currentPage--;
    }
}

function nextPage() {
    const totalPages = Math.ceil(nmbrOfPosts / itemsPerPage);
    if(currentPage < totalPages) {
        currentPage++;
    }
}

function updatePaginationDisplay() {
    const pageIndicatorRef = document.querySelector('#pageIndicator');
    pageIndicatorRef.textContent = `Sida ${ currentPage }`;
}

export default { getCurrentPage, setNmbrOfPosts, previousPage, nextPage, updatePaginationDisplay };
```

## 07-headerStyling
Lägg in följande styling i er css-fil
```
/* Page Header */
.page-header {
    width: 100%;
    background-image: url('./resources/header-background.png');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}

.page-header__title {
    padding: 8rem 0;
    font-size: 4rem;
    color: var(--heading-yellow)
;}
```

## 08-mainStyling
Lägg in följande styling i er css-fil
```
/* Main Section */
.main-section {
    background-color: var(--background-grey);
}

.main-section__wrapper {
    display: flex;
    justify-content: space-between;
}

.main-section__box {
    min-height: 60vh;
    width: 48%;
    margin-top: -4rem;
    border-radius: 2rem 2rem 0 0;
    border: 1px solid black;
    display: flex;
    flex-direction: column;
    background-color: var(--background-grey-light);
    margin-bottom: 2rem;
}

.characters__header, .details__header {
    padding: 1.5rem;
    font-size: 2rem;
    color: var(--heading-yellow);
    text-align: center;
    border-radius: 2rem 2rem 0 0;
}

.details__header {
    background-color: var(--heading-green);
}

.details__info {
    display: flex;
    flex-direction: column;
    height: 100%;
}
```

## 09-basicStyling
Lägg till följande styling i er css-fil
```
/* Characters Section */
.characters__header {
    background-color: var(--heading-grey);
}

.characters__list-item {
    list-style-type: none;
    padding: 1.3rem;
    font-size: 1.2rem;
    cursor: pointer;
}

.characters__list-item:nth-child(odd) {
    background-color: var(--darker-grey);
    color: var(--text-light);
}

.characters__list-item:nth-child(even) {
    background-color: var(--lighter-grey);
    color: var(--text-dark);
}

.characters__list-item:hover {
    background-color: var(--active-grey);
    color: var(--text-light);
}

.characters__list-item.active {
    background-color: var(--active-grey);
    color: var(--text-light);
}

/* Joint person & home styling */
.person-info, .home-info {
    flex: 1;
    padding: 1rem;
}

.person-info__name, .home-info__name {
    font-size: 1.8rem;
}

.person-info__list-item, .home-info__list-item {
    list-style-type: none;
    padding: .2rem 0;
    font-size: 1.5rem;
}

/* Person Info */
.person-info {
    background-color: var(--text-dark);
}

/* Home Info */
.home-info {
    background-color: var(--darker-grey);
    color: var(--text-light);
}
```

## 10-paginationStyling
Lägg in följande styling i er css-fil
```
/* Pagination Container */
.pagination-container {
    margin: auto;
    display: flex;
    padding: 1.5rem;
    justify-content: center;
    align-items: center;
}

.page-indicator {
    font-size: 1.5rem;
    padding: 0 1rem;
}

.pagination-btn {
    cursor: pointer;
    font-size: 1.5rem;
}
```
## 11-searchStyling
Lägg in följande styling i er css-fil
```
/* Search Section */
.search-section {
    background-color: var(--background-grey-light);
    min-height: 50vh;
}

.search-section__form {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    padding: 2rem 0;
}

.search-section__input {
    padding: 1rem;
}

.autocomplete-list {
    list-style-type: none;

}

.autocomplete-list li {
    padding: .4rem;
    cursor: pointer;
    background-color: white;
}

.autocomplete-list li:hover {
    background-color: #f4f4f4;
}
```

## 12-responsiveStyling
Lägg in följande styling i er css-fil
```
@media screen and (max-width: 800px) {
    .main-section__wrapper {
        flex-direction: column;
        align-items: center;
    }

    .main-section__box {
        width: 90%;
    }
}
```

## 13-pageSetup
Lägg in följande kod i app.js
```
pageSetup();

function pageSetup() {
    fetchCharacters();
    paginationSetup();
    
    document.querySelector('#searchInput').addEventListener('input', updateAutoCompleteList);
}
```

## 14-fecthCharacters
Fägg in följande kod i app.js
```
async function fetchCharacters() {
    let nextUrl = 'https://swapi.dev/api/people/';

    while(nextUrl) {
        const data = await apiHandler.fetchData(nextUrl);
        
        data.results.forEach(character => {
            characters.pushCharacter(character);
        });

        nextUrl = data.next;
    }

    pagination.setNmbrOfPosts(characters.getCharacters().length);
    renderCharacters();
}
```

## 15-paginationSetup
Lägg in följande kod i app.js
```
function paginationSetup() {
    const prevRef = document.querySelector('#prevPageBtn');
    const nextRef = document.querySelector('#nextPageBtn');

    prevRef.addEventListener('click', () => {
        pagination.previousPage();
        renderCharacters();
    });
    
    nextRef.addEventListener('click', () => {
        pagination.nextPage();
        renderCharacters();
    });
}
```

## 16-renderCharacters
Lägg in följande kod i app.js
```
function renderCharacters() {
    const currentPage = pagination.getCurrentPage();
    const itemsPerPage = 8;
    const startIndex = (currentPage - 1) * itemsPerPage;
    const endIndex = startIndex + itemsPerPage;
    const displayedCharacters = characters.getCharacters().slice(startIndex, endIndex);

    const listRef = document.querySelector('#charactersList');
    listRef.innerHTML = '';

    let counter = itemsPerPage;
    if(currentPage === 11) {
        counter = 2;
    }

    for(let i = 0; i < counter; i++) {
        const listItemRef = document.createElement('li');
        listItemRef.textContent = displayedCharacters[i].name;
        listItemRef.classList.add('characters__list-item');
        listRef.appendChild(listItemRef);

        listItemRef.addEventListener('click', (event) => {
            const listItemRefs = document.querySelectorAll('.characters__list-item');
            listItemRefs.forEach(ref => {
                ref.classList.remove('active');
            });

            event.target.classList.add('active');

            renderPersonDetails(displayedCharacters[i].url);
            renderHomeworldDetails(displayedCharacters[i].homeworld);
        });
    }
    pagination.updatePaginationDisplay();
}
```

## 17-functionsSetup
Lägg in följande kod i app.js
```
async function renderPersonDetails(url) {

}

async function renderHomeworldDetails(url) {

}

function updateAutoCompleteList(event) {

}
```

## 18-renderPersonDetails
Lägg till följande kod i funktionen med samma namn
```
const data = await apiHandler.fetchData(url);
const headRef = document.querySelector('#personName');
headRef.textContent = data.name;

const listRef = document.querySelector('#personInfoList');

const personListContent = `
    <li class="person-info__list-item">Height: ${data.height} cm</li>
    <li class="person-info__list-item">Mass: ${data.mass} kg</li>
    <li class="person-info__list-item">Hair Color: ${data.hair_color}</li>
    <li class="person-info__list-item">Skin Color: ${data.skin_color}</li>
    <li class="person-info__list-item">Eye Color: ${data.eye_color}</li>
    <li class="person-info__list-item">Birth Year: ${data.birth_year}</li>
    <li class="person-info__list-item">Gender: ${data.gender}</li>
`;

listRef.innerHTML = personListContent;
```

## 19-renderHomeworldDetails
Lägg till följande kod i funktionen med samma namn
```
const data = await apiHandler.fetchData(url);
console.log(data);

const headingRef = document.querySelector('#homeName');
headingRef.textContent = data.name;
const listRef = document.querySelector('#homeInfoList');

const homeListContent = `
    <li class="home-info__list-item">Rotation Period: ${data.rotation_period}h</li>
    <li class="home-info__list-item">Orbital Period: ${data.orbital_period} days</li>
    <li class="home-info__list-item">Diameter: ${data.diameter} km</li>
    <li class="home-info__list-item">Climate: ${data.climate}</li>
    <li class="home-info__list-item">Gravity: ${data.gravity}</li>
    <li class="home-info__list-item">Terrain: ${data.terrain}</li>
`;

listRef.innerHTML = homeListContent;
```

## 20-updateAutoCompleteList
Lägg till följande kod i funktionen med samma namn
```
console.log(event.target.value);

const autoCompleteList = document.querySelector('#autocompleteList');
const userInput = event.target.value.toLowerCase();

const matchedCharacters = characters.getCharacters().filter(character => character.name.toLowerCase().includes(userInput));
console.log(matchedCharacters.length);

autoCompleteList.innerHTML = '';

let maxCounter = 10;
if(matchedCharacters.length < 10) {
    maxCounter = matchedCharacters.length;
}

for(let i = 0; i < maxCounter; i++) {
    const listItemRef = document.createElement('li');
    listItemRef.textContent = matchedCharacters[i].name;
    autoCompleteList.appendChild(listItemRef);

    listItemRef.addEventListener('click', () => {
        renderPersonDetails(matchedCharacters[i].url);
        renderHomeworldDetails(matchedCharacters[i].homeworld);
        autoCompleteList.innerHTML = '';
    });
}
```
