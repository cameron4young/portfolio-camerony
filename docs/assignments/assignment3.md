---
title: Assignment 3
layout: doc
---

# Assignment 3

## Pitch

FindBuyReview is a social media application designed for older 
generations, whom are often overlooked by social media advertisers and tend to distrust conventional social media platforms. The platform is focused on empowering both users and advertisers. FindBuyReview aims to assist users in finding useful products and services that they can trust in while also giving advertisers the tools to specifically interact with user groups they fail to target on other platforms. FindBuyReview’s core functionality revolves around User Profiles, a collection of information unique to each user that the platform uses to more intelligently recommend posts and advertisements. Upon creating an account, users are (optionally) asked to input information such as age, location, interests, and favorite companies. All data used to recommend content to users is voluntarily given by users to increase trust and transparency. Users are able to edit their profiles at any time to curate their feed. To give users even more feed curation tools, users are given a ‘Looking For Product’ status which will boost posts related to their status. 

Content on the platform consists of either video reviews or paid promotions. To ensure all reviews are useful, all video reviews are required to contain a rating, caption, and a link to buy the product. Users are able to block any content on the site with ‘Already Seen’ and ‘Block’ options on every ad and post. On the advertiser end, brands are able to specifically target certain groups such as ‘people interested in beauty products over the age of 40’. Additionally, brands are able to send offers to users, where users have the opportunity to receive a discounted item in exchange for a review. This approach allows brands to leverage real user experiences to create content for audiences that are harder to reach on other platforms.


## Concepts
<h4>User Profile</h4>

  - Purpose: allow users to curate their own feed based on preferences
  - Operational Principle: after creating an account, users can specify their interests, favorite companies, and curate their own feed while using the application by blocking products or companies.

State:

    - const interests: set String
    - const age: number
    - const location: String
    - const favoriteCompanies: set String
    - const alreadySeen: set String
    - const blocked: set String

Actions:

    addInterest(interest: String):
        Adds an interest to interests set
    addFavoriteCompany(company: String):
        Adds a company to favorite Companies
    addAlreadySeen(seen: String):
        Adds seen (company or product) to already seen list
    addBlocked(block: String):
        Adds block (company or product) to blocked list
    sortPosts(posts: Set[Post]):
        Sort through set of posts, removing posts that include blocked
        or alreadySeen content, and prioritizing posts from interests and favorite companies
        Returns posts to be displayed to user
    hasInterests(potentialInterests: Set[String]):
        returns True if any potential interests overlap with interests set
        returns False if not
    likesCompany(company: Set[String]):
        returns True if any companies are in favoriteCompanies
        returns False if not
    editLocation(newLocation: String):
        location := newLocation

<br>

<h4>Direct Messaging:</h4>

- Purpose: allow users to communicate with other users and advertisers. Advertisers can send offers for users to review their products.

- Operational Principle: users can view messages in a type box, click a send button to send to others.

State:

    - const blocked: set Users
    - const messagesList: List[Message]
    - const offers: set {Offer}

Actions:

    reviewConversation(recipient: User):
        Get the current conversation from database given a recipient 
        messagesList := conversation
    sendMessage(message: String, recipient: User):
        Sends chat message to recipient
        Checks if recipient is blocked, returns 500 if so
    deleteMessage(messageId: String, recipient: User):
        Deletes message with id messageId from messages
    sendOffer(company: String, product: String, duration: number, recipient: User, deal: String):
        Sends a new offer (company, product, duration, deal) to recipient
        Expiring.add(offer, duration)
    acceptOffer(offer: Offer):
        Accept the offer
    checkOfferCompleted(post: Post):
        If post meets requirements and was posted before the offer’s duration expires, marks as complete
        If not, the offer expires

<br>

<h4>Posting:</h4>

- Purpose: allow users to upload reviews
- Operational Principle: users can record a video and publish the video with a caption, star rating, and link to the product for others to see

State:

    - const postID: String
    - const video: Video object
    - const user: User object
    - const date: Datetime object
    - const rating: Number (1-5)
    - const caption: String
    - const productURL: String
    - const postURL: String

Actions:

    post(video):
      Uploads video onto user’s profile with corresponding caption, rating, and productURL
      Creates and returns postID
    editCaption(newCaption: String):
      caption = newCaption
    editRating(newRating: Number):
      rating = newRating
    delete(video):
      Removes video and attributes from the database

<br>

<h4>Promoting:</h4>

- Purpose: make certain posts more visible than others
- Operational Principle: a promote button on every post will prompt users to fill out duration & target groups fields. After the necessary information is input, the post is given a prioritization over other posts.

State:

    - const promotedPosts: Set[Post]

Actions:

    promotePost(postID: String, targetGroup: String, duration: Integer):
      Retrieves post with postID from database
      Post.Prioritization = True
      Post.TargetGroup = this.targetGroup
      promotedPosts.add(post)
      Expiring.add(postID, duration)
    expirePromote(duration: Integer):
      this.retrievePromotedPost(postID)
      Check if any promotions are expired
      Post.Prioritization = False

<br>

<h4>Feed:</h4>

  - Purpose: allow users to browse reviews
  - Operational Principle: feeds are categorized, and each favorite category has its own button within the feed. The category’s feed is displayed when pressed. New categories can be added by clicking a button. Users see their chosen posts in a grid layout.

  State:

    - currentFeedCategory: String
    - posts: Set[Post]
    - favoriteCategories: set String

  Actions:

    addFavoriteCategory(newCategory: String):
      Add newCategory to favoriteCategories
    switchCategory(newCategory: String):
      currentFeedCategory = newCategory
    reviewNewPosts():
      Retrieve first 'n newPosts' of type feedCategory from database and returns them
    displayPosts(newPosts: Set[Post]):
      posts = newPosts

<br>

<h4>Liking:</h4>

  - Purpose: allows users to react to posts
  - Operational Principle: users press the like button on other user’s posts

  State:

    - liked: set[String]

  Actions:

    unlike(postID: String):
      Remove postID from liked
    like(postID: String):
      Adds postID to liked
    getLiked():
      Returns liked

<br>

<h4>Saving:</h4>

  - Purpose: users can save reviews to ponder purchasing a product
  - Operational Principle: users press save button on posts to put it in their collection

  State:

    - saved: Dictionary[String]

  Actions:

    unsave(postID: String, collectionName: String):
      Remove post from saved[collectionName]
    save(postID: String, collectionName: String):
      Adds postID to saved[collectionName]
    getSaved():
      Returns saved

<br>

## App-Level Actions/Synchronizations

**Sending Offers** 

Include:

- DirectMessaging
- UserProfile

sync sendOffer(company:String, product:String, duration:number, deal:String, interests: set[string], similarCompanies: set[string]):

        for user in all users:
        if UserProfile.hasInterest(interests) or UserProfile.likesCompany(similarCompanies):
                DirectMessaging.sendOffer(company:String, product:String, duration:number, user, deal)
		

**Posting Reviews**

Include:

- DirectMessaging
- Posting
- Promoting

sync postPromoted(video: Video,  targetGroup:string, duration:number):

        postId = Posting.postVideo(video)
        Promoting.promotePost(postId, targetGroup,duration)

sync postOffer(video: Video):

        postId = Posting.postVideo(video)
        retrieve post from database using postid
        DirectMessaging.checkOfferCompleted(post)


**Browsing Reviews**

Include:

- UserProfile
- Feed
- Promotion

sync createUserProfile(interests: set String, favoriteCompanies: set String):

        UserProfile.addInterest(for each interest in interests)
        UserProfile.addFavoriteCompany(for each company in favoriteCompanies)
        Feed.addFavoriteCategory(for each interest in interest)

sync createFeed(category: string):

        posts = Feed.retrieveNewPosts()
        posts := retrievePromotedPosts(category)
        UserProfile.sortFeed(posts)
        Feed.displayPosts(posts)

sync curateFeed(postID:string, action:string, category: string):

        if action == “alreadySeen”:
        Feed.addAlreadySeen(postID)
        elif action == “block”:
        Feed.addBlocked(postID)
        this.createFeed(category)

Concepts which directly translate to app-level actions: <i>Liking, Saving</i>

## Dependency Diagram
<img src="/../assets/images/a3-images/dependency.png" width="500" style="border-radius:2vh">

## Wireframes

User Profile Survey
<img src="/../assets/images/a3-images/userprofile.png" width="500" style="border-radius:2vh">

Browsing, Liking
<img src="/../assets/images/a3-images/browse.png" width="500" style="border-radius:2vh">
<img src="/../assets/images/a3-images/browse2.png" width="500" style="border-radius:2vh">
<img src="/../assets/images/a3-images/browse3.png" width="500" style="border-radius:2vh">

Posting
<img src="/../assets/images/a3-images/post.png" width="500" style="border-radius:2vh">

Direct-Messaging
<img src="/../assets/images/a3-images/messages.png" width="500" style="border-radius:2vh">
<img src="/../assets/images/a3-images/messages2.png" width="500" style="border-radius:2vh">
<img src="/../assets/images/a3-images/messages3.png" width="500" style="border-radius:2vh">
<img src="/../assets/images/a3-images/messages4.png" width="500" style="border-radius:2vh">

Settings
<img src="/../assets/images/a3-images/settings.png" width="500" style="border-radius:2vh">

Promoting
<img src="/../assets/images/a3-images/promote.png" width="500" style="border-radius:2vh">
<img src="/../assets/images/a3-images/promote2.png" width="500" style="border-radius:2vh">

Profile
<img src="/../assets/images/a3-images/profile.png" width="500" style="border-radius:2vh">

Saving
<img src="/../assets/images/a3-images/collections.png" width="500" style="border-radius:2vh">

## Design Tradeoffs

Rows of 3

- Originally, I had planned to arrange the main ‘feed’ page as carousels which were categorized under topics such as ‘Men’s Clothing’, however considering my target audience is older people, I decided that a grid layout with rows of 3 would be much more suitable. To be more precise, I feel as though the current design increases visibility of posts.

Purchasing Directly on Platform

- To make purchasing things off of the platform much easier, I previously wanted to allow users to make payments and buy directly on the platform. Considering the target audience and my concerns of over-spending brought up in the previous assignment, I decided it would be much better to add Product URLs to each post rather than allow for people to buy things directly on the platform.

Select or Swipe

- I initially wanted part of the user profile survey to include a section where users swipe on companies and products to build their profile. Considering most older people do not use applications such as Tinder, I felt as though it may be confusing to some users. Additionally, I felt as though the survey which resembled Twitter’s user survey was best for the job.
