# GPT-Param-Grid-Search

This code performs a Grid Search over parameter value combinations for the OpenAI's `ChatCompletion` endpoint:
- `temperature`
- `top_p`
- `presence_penalty`
- `frequency_penalty`

The code runs through a dataframe of lesson examples, with the columns `Concept` (String chapter name), `Text` (String lesson text), `Code` (String lesson code), making 2 API calls per param combination for each lesson. One to get the answer to a user's question, one asking the model to rate the answer, given the question and the answer received.

The output is a logs file, containing the answer to be rated, the model's rating, and its reasoning behind the rating, for each parameter combination in each lesson. 

As some lessons receive high scores easily due to their simplicity (and have several parameter combinations giving a max score), and some lessons receive high scores more seldomly, the best parameters can be chosen by filtering the logs to only contain rows with the max score (5), and then getting the param combination with the highest occurence.
