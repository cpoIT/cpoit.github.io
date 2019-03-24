# Reflections of a Fullstack Software Engineer
## Reminders International
### Week One
This week 3 other engineers and I started a new project: Reminders International. Some people get excited by the smell of a new car or unwrapping the plastic off of a new journal. For me, getting assigned to a new project is bliss. At the beginning, there are endless possibilities about how this product will look and feel like. I like imagining what it would look like if there were no constraints.  Then reality sets in and I start reviewing documentation and diagrams and piecing together all the information. We are using [Trello](https://trello.com/) to coordinate our workflow process. We created a Product Canvas (more details below) in Google Sheets and then we started cloning the near-empty Github repositories into a terminal and initializing the front and back ends on VS Code. Eventually, a new Chrome tab opens with the mesmerizing sky blue React logo with ```Welcome to React```. At this point, my fingers rest on the keyboard excited to begin the real work. 

But then, a little bit of fear starts to set in. It is the same fear people have of driving off the car lot in a new car. There is so much excitement about the journey ahead, but in the back of your mind, you are also wondering when are you going to get the first scratch or worse yet a fender bender?

#### Group Achievements
But, before discussing minor and major roadblocks, let me described a little about what I did this week. As a group, we created a Product Canvas with: 
- an Analysis of Competitor Products, 
- User Stories to highlight the why's behind the feature, 
- the Views needed to access and see these features, 
- a Database model (using [SqlDBM](https://sqldbm.com/Home/)) and mock data for 500 users (using [Mockaroo](https://www.mockaroo.com/)),
- our Architectural Recommendations, and 
- a modified Lean Canvas to summarize our results.

Along the way, it became clear that we needed to create a User Journey to coordinate the steps in terms of pages, buttons, and different journeys for the different type of users, and match them to the wireframe sketches. Instead of using a traditional flow chart, I opted to create a quick and dirty journey using Google Sheet to map out the steps that would later be used to implement a more traditional looking flowchart (using [draw.io](https://draw.io/)). By the end of the week were able to successfully deploy both the front (using [netlify](https://www.netlify.com/)) and back ends (using [Heroku](https://heroku.com)) together. We documented our personal experiences (you are reading mine now) and presented our work to others and received feedback.

#### Personal Achievement
The thing I am most proud of is deconstructing one feature (ability to create a template for a reminder) of the user story. I spent a lot of time trying to break down every step into the smallest detail. Who knew how many steps it took to add 1 checkbox on a website? As a new developer, I am astonished. A user sees a small empty box on the screen. They never consider state, how one developer needs to reach out to another since this box is on a page or model owned by another developer, researching a new library like bootstrap/reactstrap to see how it handles forms, that clicking on this box will likely necessitate a new view with its own buttons and boxes/cards, etc. that was not included in the provided wireframe and for the backend what API calls will are associated with. To be honest, do any developers really realize all these steps?

This process of investigating the user's point of view and breaking it down to the smallest minutia possible helped me realize how much important it was for us to connect and flesh out a User Journey to get a consensus for our approach and making sure that it matched the wireframe provided to us by the client in [Balsalmiq](https://balsamiq.cloud/). Sometimes, it takes examining one tree to realize that you need to see the whole forest (or Geek Speak multiple node-trees merged together).

#### Roadblocks & Solutions of How to Remove Them
Working with React there are always minor roadblocks. We used previous code and console.log to quickly rectify them. Our largest roadblock was how to seed all the variables for our mock data. We received a 'too many SQL variables' error. A quick Google search shows this is a common error for SQLite users, but the solution was not as easy to find. Since our product would eventually implement PostgreSQL, we looked into implementing that immediately instead of SQLite. However, Heroku handles SQLite to PostgreSQL interchange. 

We read more about SQLite and discovered a max of 999. Which we first interpreted to mean 999 users, which we were under since we only mocked 500 users. Then through trial and error, we realized it was 999 variables for all users. At a minimum, we needed 1000 variables since we needed an id and name for each of 500 users. 

Next, we created multiple seed files to separate the seeds into chunks. While all the seeds ran, we couldn't see all 500 users at once. Then, we looked at the [Knex documentation](https://knexjs.org/), which is extremely well organized and easy to understand. Its best feature is the 'Show example query output as:' drop-down button at the top, which changes the examples based on the product you are using (i.e., Postgres, MSSQL, MySQL, MariaDB, SQLite3, Oracle, and Amazon Redshift). After MDN, this is my favorite tech documentation site. It provided the answer: 'Unlike migrations, every seed file will be executed when you run the command. You should design your seed files to reset tables as needed before inserting data.' So, we kept .truncate() on our first seed and removed it for the remaining seeds.
