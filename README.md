# GildedRoseDevopsChallenge

Hi and welcome to team Gilded Rose.
As you know, we are a small inn with a prime location in a prominent city ran by a friendly innkeeper named Allison.
We also buy and sell only the finest goods, and we would like to advertise them to the whole world!
We just got our first capital seed to grow our business and we plan to go full digital!

We have started with two applications:
- a landing page where we can advertise our inn to the whole world
- a website where our stock manager can update our items in stock

Two small teams were hired so far, but are planning on many more!
- team Horde: builds the landing page and main website   (React SPA with no backend)
- team Alliance: builds the Stock Management application (DotNetCore website and Sql Server)

The Azure environment where they are deploying looks like this:
- Tenant
  - Subscription: GildedRoseSubscription
    - ResourceGroup: GildedRose
      - AppServicePlan
         - name: HordeTest
         - description: test web server for the Landing Page
         - plan: S1
         - cost: €72 / month
      - AppServicePlan
        - name: HoderProd
        - description: production web server for the Landing Page
        - plan: S3
        - cost: €288 / month
      - ApplicationInsights
        - name: appInsights
        - description: holds logs for both Horde and Alliance teams
      - AppServicePlan
        - name: Alliance1
        - description: web server and React spa for stock management system
        - plan: B1
        - cost: €54 / month
        - slots
          - production: serves the production Single Page Application of the Stock Management System
          - test: serves the test Single Page Application of the Stock Management System
          - jerry: Jerry created his own slot, so he can test the application in the server before deploying to test
      - Sql Server
        - name: GildedRoseSqlServer
        - description: Sql Server holding databases for the Stock Management application
      - Sql Database
        - name: StockProd
        - description: Production database for the Stock Management application
        - plan: 2 vcores, pay as you go
        - cost: €385/month
      - Sql Database
        - name: StockTest
        - description: Production database for the Stock Management application
        - plan: 2 vcores, pay as you go
        - cost: €385/month
      - AppServicePlan
        - name: AlliancePoC
        - description: web for POCs, looks like someone forgot to delete this
        - plan: S1
        - cost: €72 / month  
        
Our development teams recognize they need guidance to manage the Azure Cloud Environment.
As the founding member of the new Devops team, your first tasks are:
- define a better resource organization policy
- the teams are currently deploying the solutions from VsCode. How could they deploy in a better way?
- they complain that manually creating resources is pain and sometimes they forget to delete them. Can that be improved?
  - can you write a Terraform / ARM / Azure Devops to automate resource creations? How should it be deployed?
- GDPR is a thing here in Azeroth. Only the persons who should have access to a production resource have it. How could we restrict that?
- what other ideas do you have to make our infrastructure cheaper, more available, secure and scalable?
- keep in mind we are planning to expand and hire many more teams!
