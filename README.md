Digital Fullstack Challenge
This challenge aims to assess how you approach a problem starting from the high level solution to the low level implementation details and code quality. The points marked as (🏆 BONUS) are not required, but only optional if you want to go the extra mile. You will not be penalized for asking questions, so don't hesitate to ask us if you need any clarification.



🍿 Movie Search Site
You are asked to build a simple website that has a search box where a user will be able to search for movies by name and see the list of the results. The results will be fetched from an external API on the backend. The frontend & backend should be in the same repo for the sake of simplicity. Send the repo link or zip file in your submission.

External API
Use OMDb API to get movie search results

API docs: http://www.omdbapi.com/

Example request: http://www.omdbapi.com/?apikey=[API_KEY]&s=[KEYWORD]&page=[PAGE]

where

API_KEY: you need to get a free API key from here http://www.omdbapi.com/apikey.aspx
KEYWORD: the keyword to search by
PAGE: page number for the results, starting from 1
If you have trouble getting an API key, please reach us.

🛠 Functional Requirements
Frontend

Build a single page app with React/Redux with the following functionality

Display a search bar where a user can type a search keyword

Display the results as a grid of 3 columns, for each movie display the movie poster returned from API and the movie title below it

|-----------|  |-----------|  |-----------| 
|           |  |           |  |           | 
|   Poster  |  |   Poster  |  |   Poster  | 
|           |  |           |  |           | 
|-----------|  |-----------|  |-----------| 

   Title           Title          Title      

|-----------|  |-----------|  |-----------| 
|           |  |           |  |           | 
|   Poster  |  |   Poster  |  |   Poster  | 
|           |  |           |  |           | 
|-----------|  |-----------|  |-----------| 

   Title           Title          Title      
                 .
                 .
                 .  </code></pre></li>
On mobile screens (width <= 768px), the grid will be 2 columns


|-----------|  |-----------| 
|           |  |           | 
|   Poster  |  |   Poster  | 
|           |  |           | 
|-----------|  |-----------| 

   Title           Title    

|-----------|  |-----------| 
|           |  |           | 
|   Poster  |  |   Poster  | 
|           |  |           | 
|-----------|  |-----------| 

   Title           Title     
         .
         .
         .    </code></pre></li>
You should start to fetch and display the results from the backend once the user types 3 characters or more in the search bar


If the user is typing, don't make any API calls until they stop typing for 300ms


Consider all the possible UI states: initial, loading, error,… and present them to the user clearly. No fancy UI required


There are no design requirements, but we expect you to use minimal CSS to structure the page and make it a little pleasant. Use any CSS convention you prefer like BEM, SUITCSS,…


🏆 BONUS To track the views of each movie, we should fire an analytics event when a movie poster becomes visible to the user. If a movie poster is in the results but below the fold, the event should only fire if the user scrolls to it. Instead of calling an analytics API you can just log to the console a message like: Movie view: [The movie title]. This message should not be logged again if a user scrolls down then up again, it's only on the first view.


Backend

The NodeJS API server that will feed the data to the frontend

Endpoint /api/search?keyword=foo which will take the search keyword as a query param and return the matching results from the external API
This endpoint should return the first 20 results in 1 request, that means you need to make 2 requests to the external API as it will return only 10 results each time. Find the most efficient way to implement this and explain your solution
If a user searches for the same keyword again within 30 seconds, the request should not go the server again and should be served from the browser cache instead
Each search result should be cached on the server indefinitely and served from the cache if requested again. Use any cache library or store if you prefer
If multiple users search for the same keyword at the same time, you should call the external API once only and serve both requests with the same results
🏆 BONUS If the user searches for a keyword that is cached on the server but the results are older than 1 minute ago, serve the user the cached results immediately, and then refresh the results in the cache so the next user will get the latest results
🏆 BONUS Add an endpoint /api/cache/refresh that will loop on every keyword that is cached on the server, and refresh the results with the latest from the external API
✨ Non-Functional Requirements
README.md file explaining your high level solution and any decisions you made and the reasons behind them
A single command to run the frontend & backend. Using docker is preferred
Include unit tests. No need for full coverage. Choose some functionalities in the frontend & backend that you think need tests the most
We will assess the quality of your code. Use modern ES6+ syntax, async/await, elegant & readable code
Feel free to use any boilerplate to start the project, but remove unused code before submitting the challenge
Include the following in your README:
The time you spent on the challenge
What would you change in your submission to make it production ready?
What would you do differently if you had more time?
Clean git log is appreciated but not required
