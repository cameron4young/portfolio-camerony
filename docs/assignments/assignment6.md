---
title: Assignment 6
layout: doc
---

# Assignment 6

## Prepopulate Data

Posts were added to almost every category and offer messages were sent to user's accounts.

Posts can be viewed <a href="https://findbuyreview-front.vercel.app/">here</a>.

## Task List

| Task | Instructions | Rationale |
| :---- | :---- | :---- |
| Account Creation \+ Preferences | 1. enter your desired username and password 2. modify preferences | test if creating an account and modifying preferences is intuitive, specifically testing to see if it is easy to fill out preferences form without instruction |
| Browse Categories \+ Add/Remove from Collection | 1. search for a post within the ‘Cooking’ category 2. create and save post to a collection named ‘cooking 2024’ 3. go to new collection 4. visit the product URL from saved post 5. remove post from collection | meant to emulate a user looking for a product and saving it for later. I would like to ensure collections are easy for users to find and navigate |
| Post \+ Label Post | 1. title the post ‘Surfboard Review’ 2. submit the video link: [https://www.youtube.com/embed/AT8hGrSuXLQ?si=PL-DVnN48TP\_j9zf](https://www.youtube.com/embed/AT8hGrSuXLQ?si=PL-DVnN48TP_j9zf) 3. submit the product link: [https://www.chillisurfboards.com/surfboards/detail.php?id=18184\&direct=1\&region=aus](https://www.chillisurfboards.com/surfboards/detail.php?id=18184&direct=1&region=aus) 4. give an appropriate rating and labels and then post | test the difficulty of creating a post, examine if there are any areas which may need improving. I also would like to see the effectiveness of labels—can users actually be trusted to assign their own labels and not abuse the system? |
| Edit \+ Promote Post | 1. locate your new post and edit the title to “My New Favorite Surfboard” 2. Promote your post, including an additional label for ‘beach’  | meant to test if the author-view of posts has a nice, intuitive layout. also meant to test difficulty of promoting a post and understand if there is any confusing language/layouts for input forms. |
| Message a User | 1. locate any post on the website which intrigues you 2. message the author and ask them a question about the product | test the messaging UI, see if messaging a new user could be made easier from posts and gain insight on how that could be done |
| Receiving and Completing Offer | 1. navigate to message with ‘apple’ 2. create a review for iPhone 16 3. respond to the offer | test messaging UI, see if accessing an existing conversation is easy. additionally would like to test if offer user flow is easy and what could be added to make the offer process easier on the user end |
| Sending an Offer | 1. start a new conversation with user ‘camerony’ 2. draft an offer that expires in 3 days for 10% off JBL Flip speaker 3. send the offer after the user has responded 4. view the response post 5. accept the offer | testing difficulty of sending offers, testing if input fields are easy to understand. seeking to find what could be added to make the offer process easier on the company end. |
| Modify Preferences  | 1. block a post on your feed from being seen again 2. change your currently looking for status 3. add a new interest 4. remove a favorite company 5. add a keyword to Do Not Show 6. save preferences | testing users editing their preferences after they create their account. specifically want to see if users can easily maneuver the preferences tab, especially after already seeing it before. also want to learn whether or not the language of ‘do not show’ conveys its actual meaning |


## User Studies

User Study Participants: Wesley (47 M) and Anna (22 F)

Anna was successfully able to create an account and navigate to the preferences page. Anna did not put anything in her Do Not Show list at first, and focused more on companies rather than interests. After asking Anna to browse through posts to find one labeled ‘Cooking’, she had trouble finding the Cooking category since she had not indicated Cooking as one of her interests. It took her a minute to figure out how to utilize the search bar. Anna excelled in completing the rest of the task, which revolved around testing the Saving concept. Anna was able to easily navigate posting and labeling posts. When it came to editing and promoting a post, she was able to do so with ease and thought the forms were easy to use. However, she did make a remark saying the order and proximity of the buttons made her scared of potentially deleting her post. When tasked to message a user after viewing their post, Anna laughed after realizing she needed to copy and paste the author’s name, go to the messages tab, and then enter the author’s name. After asking about this during our debrief, she stated that it would have been better if there was a profile in which she could navigate to messaging the desired user. When responding to an offer, Anna found it frustrating that she had to go back and forth between the post she made and her messages, yet when asked about it in our debrief, she said the offer response process was fairly simple and a fun idea. Anna had trouble sending an offer, not realizing she needed to press send after. This is most likely because the buttons to create an offer and send a message are grouped together. During the debrief, Anna’s overall thoughts on the app can be summarized as ‘intriguing, but needing a few UI and bug fixes’. One thing she wished to see in the future was a feed where she could browse different brands rather than products. She had very positive things to say about the features\!

At first, Wesley was unsure of how to get to the preferences page once he signed up—he expected to be taken there right away. Wesley spent much more time filling out preferences than Anna, showing that this feature is something he and others his age value. He had ‘Cooking’ as one of his interests so he found it quite easy for him to search and add a post labeled ‘Cooking’ to a collection. Posting and labeling was not an issue for Wesley, however it did take him a while to navigate through the labels. I noticed a visible expression while he was looking at some of the labels. When asked about this during our debrief, he explained that he felt as though he should be recommended labels rather than having to browse through all of them. Wesley found the editing and promoting features super simple and transparent. One thing he noted was that when he edited the post, it asked him to edit ‘content’ rather than a ‘title’ which made things a little bit confusing. Wesley also had criticism when it came to messaging—he wishes there was a button for messaging a user from their posts and he also wishes there was a short bio so he knew he was messaging. He liked the offer system and thought highlights included the company review process and how easy it was to create them. He says to expand this feature, “there should be a button which shows all of the user’s posts on the same screen \[as the message\] so this process can be easier on the user side.” During our debrief, he stated that the app would definitely suit his social media needs, however he would like it even more if he could learn even more about the products and reviewers through descriptions and bios. All in all, Wesley seemed to enjoy the app and its features, however work can be done to make user flows more obvious and concise.

## Design Flaws/Opportunities

* Some User Flows Require Jumping Around Multiple Pages (not seamless)  
  * Some of the user flows involving messaging a user or responding to offers require jumping between the messages and feed pages  
  * This is happening because there are no built-in UI features that allow users to view posts on the messaging page and no built-in UI features that allow users to message on a post’s page.  
  * Solutions:  
    * Adding a User Profile page which allows users to view their own posts on their own page, all in one place (simplifies user flow). Adding a User Profile page would also allow for a messaging button to be added, which would allow for users to seamlessly go from viewing someone’s post to messaging them. This would also help ease concerns similar to Wesley’s that users have no clue who they are messaging.  
    * New \+ button on the user end of offers to allow users to browse their own posts in a mini window (no need to leave the messaging page to respond to an offer)  
  * Level: Physical  
  * Severity: Moderate  
* Author-View of Posts Needs Editing 
  * The spacing and ordering of buttons was difficult to use and confusing for Anna. Also, the language on the edit form, specifically the word ‘content’ instead of ‘title,’ was confusing for Wesley   
  * This is happening due to both CSS styling and choice of language that users are not accustomed to. The form language comes from the backend model of posts—’content’ was re-used from the starter code to be a title for the post.   
  * Solutions:  
    * One solution is to group together edit and delete, put the promotion button in a different location, on the same page. Also adding more spacing between edit and delete would be beneficial.  
    * Fixing language on the form to reflect what the users see rather than what is on the backend.  
  * Level: Linguistic  
  * Severity: Minor  
* Users Aren’t Guided Through User Flows  
  * There were moments in my user tests where the participants were waiting for something to happen due to them not knowing where to go next (preferences don’t automatically show up after making an account, you aren’t sent back to home once you save preferences).   
  * These issues can be attributed to lack of route redirects connected to buttons, such as a Preferences redirect upon pressing the Register button. Since not every social media app includes Preferences, most users will not fill this out or know where to find it unless they are directly brought to it.  
  * Solutions:  
    * Add a route redirect to Register button so that users are sent directly to Preferences upon making an account   
    * Add route redirect to Save Preferences button so users are sent back to home after saving preferences  
  * Level: Conceptual  
  * Severity: Major  
* User Flows Need to be More Clear and Concise  
  * There were moments where certain flows such as labeling a post with tags took much longer than I had anticipated. Some of my UI layouts require users to scan which causes user flows to take much longer than expected  
  * Others can be attributed to CSS styling, specifically poor grouping of buttons or poor layout of labels. Another contributing factor could be a lack of clear ordering in categories  
  * Solutions:  
    * Order categories on preferences and create page in alphabetical order  
    * Make messaging buttons more unique, creating a button for sending an offer and a button for sending a text message  
    * Perhaps instead of displaying a grid of categories for create page, we could suggest a few based on the title and then allow users to view a mini window of all categories  
  * Level: Physical  
  * Severity: Moderate