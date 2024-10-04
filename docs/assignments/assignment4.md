---
title: Assignment 4
layout: doc
---

# Assignment 4

## Abstract Data Models

*concept* **Preferences**  
Purpose: allow users to curate their own feed based on preferences  
Operational Principle: after creating an account, users can specify their interests, favorite companies and curate their own feed while using the application by blocking products or companies  
State:  
preferences: DocCollection\<UserPreferenceDoc\>  
UserPreferenceDoc:  
&nbsp;&nbsp;&nbsp;&nbsp;id: Preference → one ObjectId  
&nbsp;&nbsp;&nbsp;&nbsp;interests: Preference → set String  
&nbsp;&nbsp;&nbsp;&nbsp;age: Preference → one number  
&nbsp;&nbsp;&nbsp;&nbsp;location: Preference → one String  
&nbsp;&nbsp;&nbsp;&nbsp;lookingFor: Preference → one String  
&nbsp;&nbsp;&nbsp;&nbsp;favoriteCompanies: Preference → set String  
&nbsp;&nbsp;&nbsp;&nbsp;doNotShow: Preference → set String  


*concept* **Messages** (previously called Direct-Messaging)  
State:  
conversations: DocCollection\<ConversationDoc\>  
&nbsp;&nbsp;&nbsp;&nbsp;ConversationDoc:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;id: Conversation → one ObjectId  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sender: Conversation → one ObjectId  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;recipient: Conversation → one ObjectId  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;messages: Conversation → DocCollection\<MessageDoc\>  


&nbsp;&nbsp;&nbsp;&nbsp;MessageDoc:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;id: Message → one ObjectId  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;content: Message → one String  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;?offer: Message → one or none Offer object (company:String, product:String, duration:number, ?response:Offer, ?associatedPost: objectId)


*concept* **Posting**  
State:  
posts: DocCollection\<PostDoc\>  
&nbsp;&nbsp;&nbsp;&nbsp;PostDoc:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;id: Post → one ObjectId  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;video: Post → one String (URL to video hosted elsewhere)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;user: Post → one ObjectId  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;date: Post → one Datetime object  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;rating: Post → one Number (1-5)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;caption: Post → one string  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;productURL: Post → one string  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;postURL: Post → one string  


*concept* **Promoting**[objectId (of post or profile to be promoted)]  
State:  
promoted: DocCollection\<PromoteDoc\>  
&nbsp;&nbsp;&nbsp;&nbsp;PromoteDoc:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;id: Promotion → one ObjectId  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;target: Promotion → one ObjectId  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;interests: Promotion → set String  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;similarCompanies: Promotion → set String  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;duration: Promotion → one number  

*concept* **Label** (previously called Feed)  
Purpose: categorize things  
Operational Principle: things are categorized and can be viewed in a group of other things with the same category  
State:  
categories: set of Strings  
categorizedPosts: DocCollection\<CategoryDoc\>  
&nbsp;&nbsp;&nbsp;&nbsp;CategoryDoc:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;id: Category → one objectId  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;label: Category → one String (from ‘categories’)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;things: Category → set of ObjectIds  

*concept* **Saving**  
State:  
collections: DocCollection\<SaveCollectionDoc\>  
&nbsp;&nbsp;&nbsp;&nbsp;CollectionDoc:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;owner: Collection → one objectId  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: Collection → one String  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;contents: Collection → set objectId  

<img src="/../assets/images/a4-images/diagram.jpg" width="700" style="border-radius:2vh">

## Implementations

ChatGPT was used to debug & comment.

<a href="https://github.com/cameron4young/findbuyreview/commit/339a7c1c484c10f5ab1e940b317a348279383d48">Saving Concept Commit</a>

<a href="https://github.com/cameron4young/findbuyreview/commit/73652227851903eb1896a70e9b99b79fe961c5e8">Labeling Concept Commit</a>

## Deployment

<a href="https://findbuyreview.vercel.app/">FindBuyReview on Vercel</a>

## Outline of Routes

<a href="https://github.com/cameron4young/findbuyreview/commit/45b98b2eef4b5be96c224ca5de13728e845697d0">Routes GitHub Commit</a>