> Getting a lot of info all at once as I try to throw together this personal project idea I've had. Rather than create more friction for myself by deeming it necessary to carefully make note of everything I'm learning, I'm going to use this space to jot down general thoughts and ideas. Perhaps diving into more detail where it feels necessary. 

Coding moment! I just spun up *yet another* personal project with good ol' 
`npx create-next-app@latest`

I'm going to use this space to keep track of what I'm reading & learning.

NextJS is a framework built on top of react that allows frontend and backend dev in one place

The folder structure in next is important, it determines the routes

#### functionality outline
Trying to come up with the outline of how my site idea would interact with data 

Keeping it just to the scope of YouTube for now:

User profile contains list of creator handles e.g. TheYardPodcast
Each creator handle has a channelId and an uploadPlaylistId


I'm setting up database functionality and I've asked ChatGPT and Claude what the most simple and easy way to approach this is. They both independently suggested Prisma with SQLite
Prisma is an ORM that makes database management easier and SQLite is this wonderful thing I wish I knew about sooner that creates a local sql database within one simple file. Not great for scaling or security but an absolute dream for quick setup and testing like I'm doing.
I've just watched [this fireship video](https://www.youtube.com/watch?v=PGpL5hYpY1o) about SQLite and I can now confidently file this into the "I wish someone had told me about this sooner" folder
Prisma on the other had is an ORM which stands for... ~~Object Relationship Manager(?)~~ Object-Relational Mapping which basically gives you the ability to interact with your database in your programming language as opposed to having to write raw SQL 

I started with some boilerplate AI setup but quickly turned to [this video](https://www.youtube.com/watch?v=QXxy8Uv1LnQ) to continue my setup

How do I see my database? 
`npx prisma studio` is a prisma command that runs a simple local site to show the database info