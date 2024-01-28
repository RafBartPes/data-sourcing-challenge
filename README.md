# Data-Sourcing-Challenge

# Movie Reviews

## Dependencies
- Python
- pandas
- requests
- time

## Retrieving Movie Reviews from The New York Times API
1. Set the base URL for The New York Times API.
2. Filter for movie reviews with "love" in the headline:
   - `section_name` should be "Movies".
   - `type_of_material` should be "Review".
   - Use a sort filter, sorting by newest.
   - Select the following fields to return:
     - headline
     - web_url
     - snippet
     - source
     - keywords
     - pub_date
     - byline
     - word_count
3. Search for reviews published between a begin and end date.

## Retrieving Movie Data from The Movie Database (TMDB)
1. Prepare The Movie Database query using titles obtained from The New York Times.
2. For each title:
   - Make a "GET" request to TMDB API to get movie details.
   - Extract relevant information such as genres, spoken languages, and production countries.
   - Append the movie data to the `tmdb_movies_list`.
   - Print status messages for each title.

## Data Processing
1. Convert the results from The New York Times to a Pandas DataFrame using `json_normalize()`.
2. Extract the title from the "headline.main" column and save it to a new column "title".
3. Extract 'name' and 'value' from items in the "keywords" column.
4. Fix the "keywords" column by converting cells from a list to a string.
5. Create a list from the "title" column using `to_list()`.
6. Merge The New York Times reviews and TMDB DataFrames on the "title" column.
7. Remove list brackets and quotation marks on the columns containing lists:
   - Create a list of the columns that need fixing.
   - Create a list of characters to remove.
   - Loop through the list of columns to fix and characters to remove.
8. Drop the "byline.person" column.
9. Delete duplicate rows and reset the index.

## Export Data
Export the processed data to a CSV file without the index.
