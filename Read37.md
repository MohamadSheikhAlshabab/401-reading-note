# Readings: Tying it all together [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read37.md)

## Deployment

  - __Vercel (Recommended)__
    - The easiest way to deploy Next.js to production is to use the Vercel platform from the creators of Next.js.
    - Vercel is an all-in-one platform with Global CDN supporting static & Jamstack deployment and Serverless Functions.
    
    - 1 - Sign up to Vercel (no credit card is required).
    - 2 - After signing up, you’ll arrive on the “Import Project” page. Under “From Git Repository”, choose the Git provider you use and set up an integration. (Instructions: GitHub / GitLab / BitBucket).
    - 3 - Once that’s set up, click “Import Project From …” and import your Next.js app. It auto-detects that your app is using Next.js and sets up the build configuration for you. No need to change anything — everything should work just fine!
    - 4 - After importing, it’ll deploy your Next.js app and provide you with a deployment URL. Click “Visit” to see your app in production.
    
    - __DPS: Develop, Preview, Ship__
      - __Develop__: Write code in Next.js. Keep the development server running and take advantage of React Fast Refresh.
      - __Preview__: Every time you push changes to a branch on GitHub / GitLab / BitBucket, Vercel automatically creates a new deployment with a unique URL. You can view them on GitHub when you open a pull request, or under “Preview Deployments” on your project page on Vercel. Learn more about it here.
      - __Ship__: When you’re ready to ship, merge the pull request to your default branch (e.g. master). Vercel will automatically create a production deployment.
      
    - __Custom Domains__: Once deployed on Vercel, you can assign a custom domain to your Next.js app. Take a look at our documentation here.
    - __Environment Variables__: You can also set environment variables on Vercel. Take a look at our documentation here. You can then use those environment variables in your Next.js app.
    - __Automatic HTTPS__: HTTPS is enabled by default (including custom domains) and doesn't require extra configuration. We auto-renew SSL certificates. 
    
---

## PostgreSQL as a Service

  - __Fully Managed HA PostgreSQL__  
    - ElephantSQL automates every part of setup and running of PostgreSQL clusters.
    - Available on all major cloud and application platforms all over the world.
    - Let your team focus on what they do best - building your product.
    - Leave server management and monitoring to the experts.
  - __Your DBA in the Cloud__
    - ElephantSQL is hosted by PostgreSQL experts, with several years of DBA PostgreSQL experience.
    -  provide 24/7 support to thousands of customers.
  - __Automated backups__
    - Automated backups are performed every day, which is stored in a cloud file storage so that they are always accessible to you.
    - You can also use point-in-time-recovery to restore your database.
  - Feel safe when storing your data with ElephantSQL
    - Security is something we prioritize above anything else.
    - A well built environment start with high coding standards that guard against attempted security breaches.
    - Our system components undergo tests and source code reviews to assess the security before we are adding our code into production.
    - ElephantSQL is compliant with SOC 2 by AICPA. We have been audited against the Security (common criteria) and Availability Trust Services Criteria. 
    - ElephantSQL comply with the European General Data Protection Regulation (GDPR).
    - ElephantSQL uses SSL/TLS to secure data in transit.
    - SSL certificates are updated on a regular basis or in an event of a security advisory from external security centers.
    -Data can be encrypted for additional security of data at rest.
---

## Building Docker Images with heroku.yml
  - Create a heroku.yml file in your application’s root directory. 
  
                    build:
              docker:
                web: Dockerfile
            run:
              web: bundle exec puma -C config/puma.rb
  - Commit the file to your repo:`git add heroku.yml` `git commit -m "Add heroku.yml"`
  - Set the stack of your app to container:`heroku stack:set container`
  - Push your app to Heroku: `git push heroku master`
  - 
