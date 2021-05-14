# Election_Analysis

Regina Negrycz 
genglist@yahoo.com 
Module 3 Challenge 
Submitted 14 May 2021 
Due 16 May 2021 
election_analysis.txt https://github.com/genlgist/Election_Analysis/blob/main/election_analysis.txt 
election_resuts.csv https://github.com/genlgist/Election_Analysis/blob/main/election_results.csv 
README.md

# Overview of Election Audit
I needed to provide the following information to the election commission: voter turnout per county, percentage of votes per county out of the total votes and I also needed to identify the county with the highest turnout.

# Election-Audit Results

• How many votes were cast in this congressional election?
	369, 711
• Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct.
	County Votes:
	Jefferson: 10.5% (38,855)
	Denver: 82.8% (306,055)
	Arapahoe: 6.7% (24,801)
• Which county had the largest number of votes?
	Denver
• Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.
	Charles Casper Stockham: 23.0% (85,213)
	Diana DeGette: 73.8% (272,892)
	Raymon Anthony Doane: 3.1% (11,606)
• Which candidate won the election, what was their vote count, and what was their percentage of the total votes?
	Winner: Diana DeGette
	Winning Vote Count: 272,892
	Winning Percentage: 73.8%

Please refer to the Election Results file at https://github.com/genlgist/Election_Analysis/blob/main/election_analysis.txt.

# Examples of Code
I imported the csv and os dependencies:
•	import csv
•	import os

I created a variable to load to load the file with the data and to create a file to save my results.
•	file_to_load = os.path.join("Resources", "election_results.csv")
•	file_to_save = os.path.join("analysis", "election_analysis.txt")

I then created lists and dictionaries to hold the various pieces of information the Board requested.
•	candidate_options = []	list holding the names of the candidates
•	counties = []	list holding the names of the counties
•	candidate_votes = {}	dictionary holding the total votes cast per candidate
•	total_county_votes = {}	dictionary holding the total votes cast per county

I initialized variables set to zero:
•	winning_count = 0 – the number of votes for the winning candidate
•	total_votes = 0 – the number of votes in the election
•	candidate_votes[candidate_name] = 0 – the number of votes per candidate
•	total_county_votes[county_name] = 0 – the number of votes per county
•	winning_percentage = 0 – the winning percentage of votes

Variables that I increased:
•	total_county_votes[county_name] += 1 - 
•	candidate_votes[candidate_name] += 1   - a vote to that candidate's count

I checked if the candidate does not match any existing candidate and then added it to the candidate list.
        if candidate_name not in candidate_options:
            candidate_options.append(candidate_name)		

I looped through the data to get the candidate name and county name from each row:        
 candidate_name = row[2]  - the candidate name from each row.
        county_name = row[1]  - Extract the county name from each row.

I wrote an if statement that checks that if the county does not match any existing county in the county list, to add it to the list of counties.
        if county_name not in counties:
            counties.append(county_name)  

I printed to both a text file and to the terminal:
•	txt_file.write(county_results)   - print to text file
•	txt_file.write(winning_county_summary) – print to text file
•	print(county_results)   - print to terminal

I used with open() to save the results to a text file:
	with open(file_to_save, "w") as txt_file:

I calculated the percentage of votes for the county.
      	county_vote_percentage = float(county_votes) / float(total_votes) * 100
        	county_results = (
            	f"{county}: {county_vote_percentage:.1f}% ({county_votes:,})\n")

I wrote an if statement to determine the winning county and get its vote count.
        if (county_votes > last_county_votes):
            winning_county = county
        last_county_votes = county_votes

I retrieved the vote count and percentage by using an f string:
        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"\n{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

I determined the winning vote count, winning percentage, and candidate.
        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage

# Election-Audit Summary: 

The file of election results could be merged with a file of registered voters. This would allow the Board to understand what percentage of registered voters voted, get percentages of age ranges and genders as well as percentages of the number of voters that voted against their registered political  party. 