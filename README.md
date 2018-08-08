# Pipeline_As_Code
Pipeline_As_Code

# 1. Setup Jenkins LABEL
as "linux" CentOs7 I have used or you can make docker-Cloud to use it.

# 2. Maven Should be More than 3.x version
I have used maven-3.5

# 3. It will copied on Local for testing
under /tmp

# Build Setup Proccess 

1. Login you jenkins server
2. Click on "New Item"
3. Git A Name "Pipeline_as_code"
4. Go to "pipeline" section
5. select "pipeline script from SCM"
   Repository URL : https://gitURL.com
   Credentials: XXXXXXXX
   Branch Specifier (blank for 'any')	: "MASTER"
   Script Path : "Jenkinsfile"
   
# apply & Save

# Trigger Your Pipeline Build "Pipeline_as_code"

# Result would be:
    1.    Production server looks to be alive     — Print Message     <1s war
    2.    Restore files previously                _ stashed           <1s
    3.    cp x.war /tmp/production.war            — Shell Script      <1s
    4.    Deployed to production                  — Print Message       <1s
