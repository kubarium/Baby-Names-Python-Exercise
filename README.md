# Baby-Names-Python-Exercise
This is my attempt at Google's Python Exercise - https://developers.google.com/edu/python/exercises/baby-names

My version implements both Part A and B in their exercise so it accepts multiple file names either passed individually or as a wildcard selection in the form of baby*.html

Usage
-----

*python babynames.py [--summaryfile] file [file ...]*  
or
*python babynames.py [--summaryfile] file**

Since I'm running on Windows, the arguments that are passed from console in wildcard form don't get resolved to their proper values but rather market as a single file like baby*.html so Python throws an error. Additional to what the exercise suggests I had to import glob to accept such input.

Summary
-------

The whole exercise took less than 2 hours. Most of my time was spent on figuring out system integration with passed arguments. I think, in retrospect, I could have taken advantage of tuples better in finding the rank, male and female regex values. Instead of assigning the result into a generic tuple and reading the values similar to reading it like a list with [index] I should have used (rank, male, female) assignment. So the following 

    rank_male_female = re.findall("<td>(\d*)</td><td>(\S*?)</td><td>(\S*?)</td>", line)
            
    if rank_male_female:
        #register male and female rank
        rank = rank_male_female[0][0]
        male = rank_male_female[0][1]
        female = rank_male_female[0][2]

        names[male] = rank
        names[female] = rank

could have been :

    (rank,male,female) = re.findall("<td>(\d*)</td><td>(\S*?)</td><td>(\S*?)</td>", line)
            
    if rank:
        names[male] = rank
        names[female] = rank

