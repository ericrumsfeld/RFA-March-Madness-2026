📌 Overview  
This project uses a Random Forest Algorithm (machine learning model) to predict the outcomes of the NCAA D1 Men's 2026 March Madness tournament games and generate a full bracket prediction. The goal was to combine the application of some data science and statistical methods I know well with some new machine learning techniques for me in order to predict the outcomes of games in this year's tournament (NCAA D1 Men's Tournament 3/19/26-4/6/26).   

🎯 Objectives  
• Train a Random Forest Algorithm model on historic men's March Madness games from 2008-2025.  
• Incorporate key statistics leading to wins based on my own basketball knowledge.   
• Implement novel functions to simulate this year's tournament.    
• Assess the model's output and further understanding of the role of machine learning in basketball playoffs.  

🧠 Approach  
Phase 1. Data Acquisition and Management  
I acquired the necessary data for this project from prior Kaggle competitions-- uploaded by Jonathan Pilafas (https://www.kaggle.com/datasets/jonathanpilafas/2024-march-madness-statistical-analysis?resource=download ; located in /archive/DEV _ March Madness.csv) and Nishaan Amin (https://www.kaggle.com/datasets/nishaanamin/march-madness-data ; located in /amin archive/Tournament Matchups.csv).
When loading this data, I had to carefully and meticulously match team names to unite the datasets. I adjusted the dataset organization for my needs, including doubling and reversing all matchups to prevent bias from entering my model.  

Phase 2. Feature Engineering  
Instead of just considering raw statistics describing each team, I decided to view each game as a data matchup between the two teams involved. Basketball is a sport in context by necessity. So, my model takes Team A's relevant statistic and subtracts Team B's in order to calculate a RELATIVE DIFFERENCE between them. My model is trained on these differences instead of the raw statistics for each team.   
Eg. Arizona’s AdjO is 128.1, and LIU Brooklyn’s is 105.7, so in this first round matchup, Team A has a +22.4 AdjO score, likely giving them an advantage to win.   
See the ✅ Final Feature List below for more details.

Phase 3. Model  
• I used a Random Forest Classifier (from scikit-learn in Python) trained on all of the aforementioned data.  
• This outputs: the win probability for each team in a matchup, and a winner.  
• The model was deployed on all of the Round of 64 matchups in the 2026 March Madness Tournament, then again on those predicted winners for the next round, and so on until a tournament winner was predicted.   

Phase 4. Hyperparameter Tuning   
I decided to upgrade my model slightly by doing some hyperparameter tuning. This boosted my accuracy on the test set from 73.9% to 75.0%. Interestingly enough, this newly improved model actually performed worse for this year's bracket, so I commented it out and kept the more simple model in the code if you run it as is.  

Phase 5. Model Evaluation and Plotting   
• The basic model was ~74% accurate on historical matchups, near the upper limit for models I've seen on the internet currently.    
• I checked the concluded Feature Importances to make sure this model knew what it was doing. The top 3 results are reasonable: AdjO, AdjD, Seed.  
• Fortunately, the log-loss is low (0.53) and Seed is negatively correlated with winning probability, so the model is sound through these sanity checks.  
• Although not the original intent, if you hard-code in each game of the actual 2026 March Madness tournament, my simple model correctly guessed the winner 79.03% of the time.  

💪 Example Outputs   
• Kansas vs California Baptist: Kansas 84.53% | California Baptist 15.47% → Kansas  
• Georgia vs Saint Louis: Georgia 49.29% | Saint Louis 50.71% → Saint Louis  

🚀 Future Improvements  
• I toyed around a bit with adding a "Big Bracket Pool Strategy Layer" which optimizes the predicted output bracket to win a pool of 1,000+ people. Completing this code in another file I won't upload, this code allowed for more chaos in late rounds to differentiate it from other strong brackets, and it ultimately had Arizona winning it all this year. I did not win the large pool I was in unfortunately.
• Efficient function to simulate thousands of brackets, and create a new average/weighted recommended bracket.
• Greater data inclusion, and more advanced machine learning methods stacked on each other. 


💻 How to Run & Tech Used  
• I recommend you simply download the Eric RFA MM26 File and unzip locally.   
• Launch Python in whatever way is accessible to you on the RFA26_Final.ipynb file and everything in there should run smoothly.     


🏁 Takeaways  
• This model was super fun to build, and it taught me a lot about how to organize, manage, optimize, and code sports analytics predictions with the most recent available data.   
• I learned more about the ins and outs of building random forest algorithms, including how to complete efficient hyperparameter tuning to boost model accuracy.     
• This model would have unethically decimated my family's bracket pool, so I'll continue to stick to my predictions I make with my own heart and eye test while watching those teams there.   
• I hope to build more novel sports analytics data solutions like this one in exciting upcoming projects!    


✅ Final Feature List  
Please keep in mind that for each matchup fed to the model, I trained and evaluated the outcomes of each game based on the DIFFERENCE between the two teams in question's stats.   
• Adjusted Offensive Efficiency [From kenpom; see source for description]    
• Adjusted Defensive Efficiency [From kenpom; see source for description]  
• AdjTempo [From kenpom; a measure of how fast each team plays]  
• FG2Pct       
• FG3Pct  
• FTPct  
• BlockPct  
• StlRate  
• FG3Rate  
• OppFG2Pct   
• OppFG3Pct   
• OppBlockPct  
• OppStlRate  
• OppFG3Rate   
• Experience  
• Bench  
• Active Coaching Length Index   
• Seed  
• ORPct  



      
👤 Author  
Eric Rumsfeld  
M.S. in Astronomy | Data Science & Sports Analytics  
