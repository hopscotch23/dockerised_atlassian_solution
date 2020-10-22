# dockerised_atlassian_solution
Objectives:
  *Starting up Jira, Confluence and Bitbucket on your client machine using Docker
  *Installing each single product
  *Setting up integrations between products
  
1. Install Docker (may require bios tweak to enable secure vm building)
2. open command prompt (win + r then "cmd")
	docker run -d -p 8080:8080 atlassian/jira-software:latest
	docker run -d -p 8090:8090 atlassian/confluence-server:latest
	docker run -d -p 8095:8095 atlassian/crowd:latest
		jira : http://localhost:8080
		confluence : http://localhost:8090
		crowd: http://localhost:8095

3.Set up each instance in an evaluation mode, following the steps in the set up guide.

4.create a new directory and place the two files 'nginx.conf' and 'docker-compose.yaml' in there

5.Open cmd, and navigate to the directory you just made with 'cd <filepath>'
then run 'docker-compose up -d'
 
6.You should then be able to open your web browser and navigate to http://jira.internal to get to Jira once it boots.
If you are receiving nginx errors such as 'Bad Gateway' then some configuration may be incorrect.
It is likely this is an error in the hosts file so navigate to C:\Windows\System32\drivers\etc and add:
127.0.0.1 jira.internal
127.0.0.1 confluence.internal
127.0.0.1 crowd.internal
