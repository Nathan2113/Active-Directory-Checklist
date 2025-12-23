MAKE SURE BLOODHOUND IS UP AND RUNNING WITH THE DOMAIN INFO
clone PlumHound into the /opt directory then run “sudo pip3 install -r requirements.txt”
“sudo python3 PlumHound.py —easy -p neo4j1”
- if it runs correctly it will give a confirmation
![Untitled 18.png](/Untitled%2018.png)
once confirmed that it is running correctly, run
- “sudo python3 PlumHound.py -x tasks/default.tasks -p neo4j1”
    
    - then cd into /opt/PlumHound/reports
    
    - open the index.html to see the whole report
    
![Untitled 1 6.png](/Untitled%201%206.png)
click details to see information
![Untitled 2 6.png](/Untitled%202%206.png)