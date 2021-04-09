# Working with Known JSON Schemas - Lab

## Introduction
In this lab, you'll practice working with JSON files whose schema you know beforehand.

## Objectives
You will be able to:
* Use the JSON module to load and parse JSON documents
* Extract data using predefined JSON schemas
* Convert JSON to a pandas dataframe

## Reading a JSON Schema

Here's the JSON schema provided for a section of the NY Times API:
<img src="images/nytimes_movie_schema.png" width=500>

or a fully expanded view:

<img src="images/nytimes_movie_schema_detailed.png" width=500>

You can more about the documentation [here](https://developer.nytimes.com/docs/movie-reviews-api/1/routes/reviews/%7Btype%7D.json/get).

Note that **this is a different schema than the schema used in the previous lesson**, although both come from the New York Times.

## Loading the JSON Data

Open the JSON file located at `ny_times_movies.json`, and use the `json` module to load the data into a variable called `data`.


```python
import json
with open('ny_times_movies.json', 'r') as f:
    data = json.load(f)
```

Run the code below to investigate its contents:


```python
print("`data` has type", type(data))
print("The keys are", list(data.keys()))
```

    `data` has type <class 'dict'>
    The keys are ['status', 'copyright', 'has_more', 'num_results', 'results']


## Loading Results

Create a variable `results` that contains the value associated with the `'results'` key.


```python
results = data['results']
```

Below we display this variable as a table using pandas:


```python
import pandas as pd
df = pd.DataFrame(results)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>display_title</th>
      <th>mpaa_rating</th>
      <th>critics_pick</th>
      <th>byline</th>
      <th>headline</th>
      <th>summary_short</th>
      <th>publication_date</th>
      <th>opening_date</th>
      <th>date_updated</th>
      <th>link</th>
      <th>multimedia</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Can You Ever Forgive Me</td>
      <td>R</td>
      <td>1</td>
      <td>A.O. SCOTT</td>
      <td>Review: Melissa McCarthy Is Criminally Good in...</td>
      <td>Marielle Heller directs a true story of litera...</td>
      <td>2018-10-16</td>
      <td>2018-10-19</td>
      <td>2018-10-17 02:44:23</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Charm City</td>
      <td></td>
      <td>1</td>
      <td>BEN KENIGSBERG</td>
      <td>Review: ‘Charm City’ Vividly Captures the Stre...</td>
      <td>Marilyn Ness’s documentary is dedicated to the...</td>
      <td>2018-10-16</td>
      <td>2018-04-22</td>
      <td>2018-10-16 11:04:03</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Horn from the Heart: The Paul Butterfield Story</td>
      <td></td>
      <td>1</td>
      <td>GLENN KENNY</td>
      <td>Review: Paul Butterfield’s Story Is Told in ‘H...</td>
      <td>A documentary explores the life of the blues m...</td>
      <td>2018-10-16</td>
      <td>2018-10-19</td>
      <td>2018-10-16 11:04:04</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>The Price of Everything</td>
      <td></td>
      <td>0</td>
      <td>A.O. SCOTT</td>
      <td>Review: ‘The Price of Everything’ Asks $56 Bil...</td>
      <td>This documentary examines the global art marke...</td>
      <td>2018-10-16</td>
      <td>2018-10-19</td>
      <td>2018-10-16 16:08:03</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Impulso</td>
      <td></td>
      <td>0</td>
      <td>BEN KENIGSBERG</td>
      <td>Review: ‘Impulso’ Goes Backstage With a Flamen...</td>
      <td>This documentary follows Rocío Molina, a cutti...</td>
      <td>2018-10-16</td>
      <td>None</td>
      <td>2018-10-16 11:04:03</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Watergate</td>
      <td></td>
      <td>1</td>
      <td>A.O. SCOTT</td>
      <td>Review: ‘Watergate’ Shocks Anew With Its True ...</td>
      <td>Charles Ferguson delivers a comprehensive docu...</td>
      <td>2018-10-11</td>
      <td>2018-10-12</td>
      <td>2018-10-17 02:44:21</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Barbara</td>
      <td></td>
      <td>1</td>
      <td>GLENN KENNY</td>
      <td>Review: In ‘Barbara,’ a Fictional Biopic of a ...</td>
      <td>It’s a film of scenes rather than of one unifi...</td>
      <td>2018-10-11</td>
      <td>None</td>
      <td>2018-10-17 02:44:21</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Over the Limit</td>
      <td></td>
      <td>1</td>
      <td>JEANNETTE CATSOULIS</td>
      <td>Review: A Russian Gymnast Goes ‘Over the Limit’</td>
      <td>Margarita Mamun endures injury and abuse in Ma...</td>
      <td>2018-10-11</td>
      <td>2018-10-05</td>
      <td>2018-10-17 02:44:20</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>8</th>
      <td>The Kindergarten Teacher</td>
      <td>R</td>
      <td>1</td>
      <td>JEANNETTE CATSOULIS</td>
      <td>Review: The Disturbing Obsession of ‘The Kinde...</td>
      <td>Maggie Gyllenhaal is riveting as a dissatisfie...</td>
      <td>2018-10-11</td>
      <td>2018-10-12</td>
      <td>2018-10-17 02:44:19</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Classical Period</td>
      <td></td>
      <td>1</td>
      <td>BEN KENIGSBERG</td>
      <td>Review: In ‘Classical Period,’ a Deep Dive — R...</td>
      <td>This highly original feature is technically in...</td>
      <td>2018-10-11</td>
      <td>None</td>
      <td>2018-10-17 02:44:18</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Bad Times at the El Royale</td>
      <td>R</td>
      <td>0</td>
      <td>MANOHLA DARGIS</td>
      <td>Review: Hard-Boiled Play in ‘Bad Times at the ...</td>
      <td>The writer-director Drew Goddard has fun with ...</td>
      <td>2018-10-11</td>
      <td>2018-10-12</td>
      <td>2018-10-17 02:44:22</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Beautiful Boy</td>
      <td>R</td>
      <td>0</td>
      <td>A.O. SCOTT</td>
      <td>Review: In ‘Beautiful Boy,’ a Writer Confronts...</td>
      <td>Two memoirs are brought to the screen in a fat...</td>
      <td>2018-10-11</td>
      <td>2018-10-12</td>
      <td>2018-10-17 02:44:21</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>12</th>
      <td>The Oath</td>
      <td>R</td>
      <td>0</td>
      <td>GLENN KENNY</td>
      <td>Review: In ‘The Oath,’ a Pledge of Allegiance ...</td>
      <td>This satirical comedy, written, directed by an...</td>
      <td>2018-10-11</td>
      <td>2018-10-12</td>
      <td>2018-10-17 02:44:21</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Bikini Moon</td>
      <td></td>
      <td>0</td>
      <td>KEN JAWOROWSKI</td>
      <td>Review: ‘Bikini Moon’ Finds a Documentary Crew...</td>
      <td>Condola Rashad plays the title character, a ho...</td>
      <td>2018-10-11</td>
      <td>2018-10-12</td>
      <td>2018-10-17 02:44:20</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Goosebumps 2: Haunted Halloween</td>
      <td>PG</td>
      <td>0</td>
      <td>TEO BUGBEE</td>
      <td>Review: ‘Goosebumps 2: Haunted Halloween’ Is T...</td>
      <td>This sequel to the movie adaptation of R.L. St...</td>
      <td>2018-10-11</td>
      <td>2018-10-12</td>
      <td>2018-10-17 02:44:20</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>15</th>
      <td>The Sentence</td>
      <td></td>
      <td>0</td>
      <td>KEN JAWOROWSKI</td>
      <td>Review: In ‘The Sentence,’ a Woman Gets Prison...</td>
      <td>The documentary denounces minimum sentencing l...</td>
      <td>2018-10-11</td>
      <td>2018-10-12</td>
      <td>2018-10-17 02:44:19</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>16</th>
      <td>All Square</td>
      <td></td>
      <td>0</td>
      <td>GLENN KENNY</td>
      <td>Review: In ‘All Square,’ Taking Big Bets on Yo...</td>
      <td>Michael Kelly, Pamela Adlon and Josh Lucas enh...</td>
      <td>2018-10-11</td>
      <td>None</td>
      <td>2018-10-11 11:04:11</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Sadie</td>
      <td></td>
      <td>0</td>
      <td>KEN JAWOROWSKI</td>
      <td>Review: The Drama ‘Sadie’ Finds a Teenager in ...</td>
      <td>The film stars Sophia Mitri Schloss as the tit...</td>
      <td>2018-10-11</td>
      <td>2018-10-12</td>
      <td>2018-10-11 11:04:07</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>18</th>
      <td>After Everything</td>
      <td></td>
      <td>0</td>
      <td>TEO BUGBEE</td>
      <td>Review: In ‘After Everything,’ a Young Love Bl...</td>
      <td>This cancer drama focuses less on the high sta...</td>
      <td>2018-10-11</td>
      <td>2018-10-12</td>
      <td>2018-10-17 02:44:18</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
    <tr>
      <th>19</th>
      <td>First Man</td>
      <td>PG-13</td>
      <td>0</td>
      <td>A.O. SCOTT</td>
      <td>Review: ‘First Man’ Takes a Giant Leap for Man...</td>
      <td>Damien Chazelle’s sweeping and intimate yet un...</td>
      <td>2018-10-10</td>
      <td>2018-10-12</td>
      <td>2018-10-17 02:44:18</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
    </tr>
  </tbody>
</table>
</div>



## Data Analysis

Now that you have a general sense of the data, answer some questions about it.

### How many results are in the file?

The metadata says this:


```python
data['num_results']
```




    20



Double-check that by looking at `results`. Does it line up?


```python
print("The length of `results` is", len(results))
print("That length equals the 'num_results value?'", len(results) == data['num_results'])
```

    The length of `results` is 20
    That length equals the 'num_results value?' True



```python
"""
Yes, the length of the `results` list matches the 'num_results'
reported by the metadata
"""
```

### How many unique critics are there?

A critic's name can be identified using the `'byline'` key. Assign your answer to the variable `unique_critics`.


```python

# Base Python solution:
unique_critics_set = set()
for result in results:
    unique_critics_set.add(result["byline"])
unique_critics = len(unique_critics_set)

# Pandas solution
unique_critics = df["byline"].nunique()

unique_critics
```




    7



This code checks your answer.


```python
assert unique_critics == 7
```

## Flattening Data

Create a list `review_urls` that contains the URL for each review. This can be found using the `'url'` key nested under `'link'`.


```python

# First, exploring the structure a bit more to make
# sure we understand it

results[0]['link']
```




    {'type': 'article',
     'url': 'http://www.nytimes.com/2018/10/16/movies/can-you-ever-forgive-me-review-melissa-mccarthy.html',
     'suggested_link_text': 'Read the New York Times Review of Can You Ever Forgive Me'}




```python

# In base Python, we can make the list with list comprehension
review_urls = [result['link']['url'] for result in results]
review_urls
```




    ['http://www.nytimes.com/2018/10/16/movies/can-you-ever-forgive-me-review-melissa-mccarthy.html',
     'http://www.nytimes.com/2018/10/16/movies/charm-city-review-baltimore.html',
     'http://www.nytimes.com/2018/10/16/movies/horn-from-the-heart-review-paul-butterfield.html',
     'http://www.nytimes.com/2018/10/16/movies/the-price-of-everything-review-documentary.html',
     'http://www.nytimes.com/2018/10/16/movies/impulso-review-documentary.html',
     'http://www.nytimes.com/2018/10/11/movies/watergate-review-documentary.html',
     'http://www.nytimes.com/2018/10/11/movies/barbara-review.html',
     'http://www.nytimes.com/2018/10/11/movies/over-the-limit-review.html',
     'http://www.nytimes.com/2018/10/11/movies/the-kindergarten-teacher-review.html',
     'http://www.nytimes.com/2018/10/11/movies/classical-period-review.html',
     'http://www.nytimes.com/2018/10/11/movies/bad-times-at-the-el-royale-review.html',
     'http://www.nytimes.com/2018/10/11/movies/beautiful-boy-review-steve-carell.html',
     'http://www.nytimes.com/2018/10/11/movies/the-oath-review-tiffany-haddish.html',
     'http://www.nytimes.com/2018/10/11/movies/bikini-moon-review.html',
     'http://www.nytimes.com/2018/10/11/movies/goosebumps-2-haunted-halloween-review.html',
     'http://www.nytimes.com/2018/10/11/movies/the-sentence-review.html',
     'http://www.nytimes.com/2018/10/11/movies/all-square-review.html',
     'http://www.nytimes.com/2018/10/11/movies/sadie-review.html',
     'http://www.nytimes.com/2018/10/11/movies/after-everything-review.html',
     'http://www.nytimes.com/2018/10/10/movies/first-man-review-ryan-gosling-damien-chazelle.html']




```python

# Alternatively, we can use pandas with a lambda function
review_urls = list(df['link'].apply(lambda links: links['url']))
review_urls
```




    ['http://www.nytimes.com/2018/10/16/movies/can-you-ever-forgive-me-review-melissa-mccarthy.html',
     'http://www.nytimes.com/2018/10/16/movies/charm-city-review-baltimore.html',
     'http://www.nytimes.com/2018/10/16/movies/horn-from-the-heart-review-paul-butterfield.html',
     'http://www.nytimes.com/2018/10/16/movies/the-price-of-everything-review-documentary.html',
     'http://www.nytimes.com/2018/10/16/movies/impulso-review-documentary.html',
     'http://www.nytimes.com/2018/10/11/movies/watergate-review-documentary.html',
     'http://www.nytimes.com/2018/10/11/movies/barbara-review.html',
     'http://www.nytimes.com/2018/10/11/movies/over-the-limit-review.html',
     'http://www.nytimes.com/2018/10/11/movies/the-kindergarten-teacher-review.html',
     'http://www.nytimes.com/2018/10/11/movies/classical-period-review.html',
     'http://www.nytimes.com/2018/10/11/movies/bad-times-at-the-el-royale-review.html',
     'http://www.nytimes.com/2018/10/11/movies/beautiful-boy-review-steve-carell.html',
     'http://www.nytimes.com/2018/10/11/movies/the-oath-review-tiffany-haddish.html',
     'http://www.nytimes.com/2018/10/11/movies/bikini-moon-review.html',
     'http://www.nytimes.com/2018/10/11/movies/goosebumps-2-haunted-halloween-review.html',
     'http://www.nytimes.com/2018/10/11/movies/the-sentence-review.html',
     'http://www.nytimes.com/2018/10/11/movies/all-square-review.html',
     'http://www.nytimes.com/2018/10/11/movies/sadie-review.html',
     'http://www.nytimes.com/2018/10/11/movies/after-everything-review.html',
     'http://www.nytimes.com/2018/10/10/movies/first-man-review-ryan-gosling-damien-chazelle.html']



The following code will check your answer:


```python

# review_urls should be a list
assert type(review_urls) == list

# The length should be 20, same as the length of reviews
assert len(review_urls) == 20

# The data type contained should be string
assert type(review_urls[0]) == str and type(review_urls[-1]) == str

# Spot checking a specific value
assert review_urls[6] == 'http://www.nytimes.com/2018/10/11/movies/barbara-review.html'
```

## Summary
Well done! In this lab you continued to practice extracting and transforming data from JSON files with known schemas.
