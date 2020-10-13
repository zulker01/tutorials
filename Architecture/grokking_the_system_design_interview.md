# Grokking the System Design Interview #
## System Design Problems ##
### System Design Interviews: A Step by Step Guide ###
1. Topics:
	1. Step 1: Requirements Clarifications
	2. Step 2: Back-of-the-envelope Estimation
	3. Step 3: System Interface Definition
	4. Step 4: Defining Data Model
	5. Step 5: High-Level Design
	6. Step 6: Detailed Design
	7. Step 7: Identifying and Resolving Bottlenecks
	8. Summary
2. Software engineers struggle with system design interviews (SDIs) due to
	1. Unstructured nature of SDIs - open-ended design problem that doesn't have a standard answer
	2. Lack of experience in developing complex, large scale systems
	3. No enough preparation for SDIs
3. This needs deliberate preparation as in coding interviews - Google, Facebook, Amazon, Microsoft, ... needs it
	1. Needs above average performance in the top companies
		1. Good performance can give higher position and higher salary (shows candidate's ability to handle complex systems)

#### Step by Step Approach to Solve Design Problems ####
##### Step 1: Requirements Clarifications #####
1. Ask about exact scope of the problem
	1. **Clarify ambiguities** early in the interview is critical
		1. If end goals of a system are defined clearly then success is more likely
	2. Clarify essential **parts of system that needs to be focussed** on in 35-40 minutes interview
2. Example: Twitter like service
	1. Questions to ask:
		1. Will users of service be able to post tweets and follow other people?
		2. Should we also design to construct and display user's timeline?
		3. Will tweets contain photos and videos?
		4. Are we focusing on backend only or are we developing front-end too?
		5. Will users be able to search tweets?
		6. Do we need to display hot trending topics?
		7. Will there be any push notification for new (or important) tweets?
	2. The questions determine how our end design will look like

##### Step 2: Back-of-the-envelope Estimation #####
1. Scale of system being design needs to be estimated
	1. Helps later when focusing on
		1. Scaling
		2. Partitioning
		3. Load balancing
		4. Caching
	2. Questions:
		1. What scale is expected from the system (e.g., number of new tweets, number of tweet views, number of timeline generations per sec., etc.)?
		2. How much storage will we need? We will have different storage requirements if users can have photos and videos in their tweets
		3. What network bandwidth usage are we expecting? This will be crucial in deciding how we will manage traffic and balance load between servers

##### Step 3: System Interface Definition #####
1. Define APIs expected from system
	1. Establishes exact contract
	2. Ensures that requirements have got validated
	3. Examples:
			
			postTwee(user_id, tweet_data, tweet_location, user_location, timestamp, ...)
			generateTimeline(user_id, current_time, user_location, ...)
			markTweetFavorite(user_id, tweet_id, timestamp, ...)

##### Step 4: Defining Data Model #####
1. Defining data model in early part of interview will clarify how data will flow between different components of system
	1. Also helps in data partitioning and management later
		1. Need to identify entities of the system
		2. Need to identify how the entities interact with each other
		3. Need to identify different aspects of management
			1. Storage
			2. Transportation
			3. Encryption
			4. ...
	2. Example: Twitter
		1. User: UserID, Name, Email, DoB, CreationData, LastLogin, etc...
		2. Tweet: TweetID, Content, TweetLocation, NumberOfLikes, TimeStamp, etc...
		3. UserFollow: UserID1, UserID2
		4. FavoriteTweets: UserID, TweetID, TimeStamp
2. Implementation:
	1. Which database system should we use?
		1. Will NoSQL like Cassandra best fit our needs?
		2. Should we use MySQL-Like solution?
		3. Which type of block storage should we use for photos and videos?

##### Step 5: High-Level Design #####
1. Draw block diagram with 5-6 boxes representing core components of system
	1. Enough components need to be drawn to solve the actual problem from end-to-end
2. Example: For Twitter
	1. We might need multiple application servers for
		1. Read/write requests
		2. Load balancers in front of them for traffic distributions
			1. If more reads than writes are expected, separate servers may be planned for them
		3. An efficient database is required for persistence (to store all tweets, support huge number of reads)
			1. Distributed file storage system may be required for photos and videos
3. High level design of twitter:

	![high_level_design_of_twitter](high_level_design_of_twitter.html) 

##### Step 6: Detailed Design #####
1. Dig deeper into two or three major components
	1. Interviewer's feedback usually guides us to different parts of the system for further discussion
	2. We may be able to present different approaches
		1. Also discuss pros and cons
			1. Justify why we prefer one approach on the other
				1. Discuss tradeoffs clearly and keep system constraints in mind
2. Constraints:
	1. For massive amount of data
		1. How to partition data to distribute it to multiple databases?
		2. Should we store all data of user on same database?
			1. Does it cause issues?
	2. How to handle hot users who tweet a lot or follow lots of people?
	3. User's timeline can contain the most recent tweets (and relevant)
		1. Does it need storing data in a way that is optimized for scanning latest tweets?
	4. To which layer cache can be introduced to speed up?
	5. What components need good load balancing?

##### Step 7: Identifying and Resolving Bottlenecks #####
1. Discuss bottlenecks and mitigation strategy
	1. Is there single point of failure in system?
	2. What are we doing to mitigate them?
	3. Do we have enough replicas of data?
		1. If we lose a few servers, can we still server users?
	4. Do we have different copies of services running?
		1. A few failures should not cause total system shutdown
	5. How is performance of service monitored?
		1. Do we get alerts when critical components fail?
		2. Do we get alerts when performance degrades?

##### Summary #####
1. For success in system design interviews:
	1. Preparation
	2. Being organized
2. The above steps can be followed to stay on track and cover all different aspects while designing a system

### Designing a URL Shortening Service Like TinyURL ###
1. TinyURL short description:
	1. Service will provide short aliases redirecting to long URLs
2. Examples: bit.ly, goo.gl, qlink.me, ...
3. Difficulty level: Easy
4. Topics
	1. Why do we need URL shortening?
	2. Requirements and Goals of the System
	3. Capacity Estimation and Constraints
	4. System APIs
	5. Database Design
		1. Database Schema
	6. Basic System Design and Algorithm
	7. Encoding Actual URL
	8. Generating Keys Offline
	9. Data Partitioning and Replication
	10. Cache
	11. Load Balancer (LB)
	12. Purging or DB Cleanup
	13. Telemetry
	14. Security and Permissions

#### Why do we need URL shortening? ####
1. URL shortening is used to construct shorter aliases for long URLs
	1. Short links
2. Users are redirected to original URL when they hit short links
3. Advantages:
	1. Save space when
		1. Displayed
		2. Printed
		3. Messaged
		4. Tweeted
	2. Less likely to mistype shorter URLs
4. Examples:

		https://www.educative.io/collection/page/5668639101419520/5649050225344512/5668600916475904/
		
		shortened to:
		
		http://tinyurl.com/jlg8zpc
		
	1. It is nearly 1/3rd the size of actual URL
5. The service is used to optimize links across devices
	1. Utility:
		1. Tracking individual links to analyze audience and campaign performance
		2. Hiding original URLs
6. [tinyurl.com](http://tinyurl.com/)
	1. Spend time on options their service offers

#### Requirements and Goals of the System ####
1. Note:

		You should always clarify requirements at the beginning of the interview. Be sure to ask questions to find the exact scope of the system that the interviewer has in mind
		
2. URL shortening system should meet the following functional requirements:
	1. Given a URL, service should generate shorter and unique alias of it (called short link)
	2. Link should be short enough to be easily copied and pasted into applications
	3. When users access a short link, service should redirect them to original link
	4. Users should optionally be able to pick custom short link for URL
	5. Links will expire after standard default timespan.
		1. Users can specify expiration time
3. Non-functional requirements:
	1. System should be highly available
		1. If service is down, URL redirections will start failing
	2. URL redirection should happen in real-time with minimal latency
	3. Shortened links should not be guessable (not predictable)
4. Extended Requirements:
	1. Analytics; e.g. how many times a redirection happened?
	2. Service should be accessible through REST APIs by other services

#### Capacity Estimation and Constraints ####

#### System APIs ####

#### Database Design ####

#### Basic System Design and Algorithm ####

#### Data Partitioning and Replication ####

#### Cache ####

#### Load Balancer (LB) ####

#### Purging or DB Cleanup ####

#### Telemetry ####

#### Security and Permissions ####

### Designing Pastebin ###
### Designing Instagram ###
### Designing Dropbox ###
### Designing Facebook Messenger ###
### Designing Twitter ###
### Designing Youtube or Netflix ###
### Designing Typeahead Suggestion ###
### Designing an API Rate Limiter ###
### Designing Twitter Search ###
### Designing a Web Crawler ###
### Designig Facebook's Newsfeed ###
### Designing Yelp or Nearby Friends ###
### Designing Uber Backend ###
### Design Ticketmaster ###
### Additional Resources ###

## Glossary of System Design Basics ##
### System Design Basics ###
### Key Characteristics of Distributed Systems ###
### Load Balancing ###
### Caching ###
### Data Partitioning ###
### Indexes ###
### Proxies ###
### Redundancy and Replication ###
### SQL vs. NoSQL ###
### CAP Theorem ###
### Consistent Hashing ###
### Long-Polling vs WebSockets vs Server-Send Events ###

## Appending ##
### Contact Us ###
### Other Courses ###