# 1. Greeting & Introduction (10min.

### #1
Thank you for joining .Net Conf 2023 Seoul and our session today, also I would like to appreciate DotNetDev community to organize this awsome event. In this session, I'm going to talk about performance tips that I want you to know before starting to develop Blazor web application, it includes some basic web knowledge and basic Blazor function, so this session will be help for beginner of developing web application using C#.

---

### #2
First of all, I'm going to introduce myself. My name is Motoki Nakae, came from Tokyo, Solutions Consultant at Infragistics, I work every day to solve customer's UI/UX problems with our knowledge and products. Since I used to be a web app developer before, I often have conversation with customers who have problem around web app development. And you can see the photo with me and my dog, his name is Matthew. If you are having a trouble around UI/UX or want to see a lot of pictures of Matthew, please get in touch with me via email or my twitter account.

---

### #3
CEO of Infragistics Japan, Ken Azuma and I flighted to Korea for this event. Also, we sponsored for snack, and we are opening a booth today, so if you have a question about my session or curios about our products, please come to our booth table, we have Korean sales guy, Dongsu Jo, so you don't have to worry about the language.

---

### #4
Just give me a few minutes to explain our company, we are Infragistics that provide well designed and high functional UI controls and components for developers all over the world for over 30 years. Especially, we contribute to .NET development experience for a long time, you can use our controls in your WPF, Windows Forms, ASP.NET, and Blazor project.

---

### #5
As you can see, we have a lot of major clients in worldwide, more than 5,000 clients in Japan, more than 60,000 clients all over the world so far. You can see some famous Korean company's logo here.

---

### #6
As I told already, having a conversation with developer, of course including .NET developer, and hearing concern or problem is my daily work. Last year, we had meeting with customers 246 times in Japan.  Honestly, I was worried about what content to be helpful for attendees in this conference, what can I tell for you. My answer is to share the common scenario that Japanese .NET developers are facing, would be a unique and useful to you, because you can refer the story that happen in other country.

---

### #7
In Japan, exactly demand of Blazor was increased 2022, as you can see 44% of 246 meetings, the customer was interested in Blazor, most of them said "we have to begin web application development, we are looking for which framework is the best, how about Blazor?" I heard hundred times kind of this question.

---

### #8
I'm going to introduce one of common scenario in Japan, the developer works for implementing desktop application for the system inside a plant or factory. The plant produces huge amount of data for 24 hours a day, then their manager wants to see these data in dashboard inside an application, for example, to see a defective rate of products or something. Because of the manager have to move around a lot during their business time, doesn't settle down to same place, this is because they want a web application to access from anywhere, anytime. 

And also, if this is the first challenge to develop the web application for them, they were concerning whether the web application works with good performance or not. this story from a lot of difference customer last year, how about you? You might face the same situation as this.

---

### #9
This introduction has become quite long, but there are today's topics. in the beginning, I'm going to talk about the reason why I recommend you Blazor quickly, next, I'd like to show the points you should take care for web application's performance, then, I'm going to show you the one of Blazor's tips for improving performance. after that, I I'm going to show you the solution if your app needs more complex functional UI components without performance issue. So, let's go to the next slide.

---

# 2. Why you should choice Blazor (5min.

### #10
Perhaps, in this kind of conference, you have seen same content several times, so I just summarized why you should choice Blazor in this slide. Firstly, you must be familiar with C#, so Blazor is good to you, you can write a code that not only back end but also front end with C#. It means you don't have to learn about JavaScript or TypeScript from the beginning to start to creating web app. Next, many Japanese our customer match this scenario, since they develop client server model for a long time, it is easy to adapt Blazor Server for them. 

Then, you can create Single Page Web Application with Blazor, in addition, PWA or MAUI Blazor App can be created. 

As showcase perspective, as I told you, a lot of companies have selected Blazor in Japan, and also in all over the globe, documents or YouTube video or some kind of reference information are increasing. 

Then, Microsoft and other library vendors including Infragistics are paying a lot of attention to Blazor, this is an another important information to you, I talked with Microsoft Japan team before, they said they are going to recommend Blazor instead of Web Forms and MVC. 

---

### #11
From the several perspectives, I can confidently say "Now, the time to start Blazor".

---

# 3. The Points of web app performance (10min.

### #12
Following these reasons, I recommended Blazor to the customer in Japan, then, as I told you, most of them take care of the performance if they try to develop Blazor web app. Indeed, there are differences between Desktop and Web application performance tuning. So, I'm going to explain about three points that you should care of your web application.

---

### #13
First point is Load Time Performance, this is about how fast your web application load, for a desktop app, the time to execute the application and be able to start interaction for user, for a web app, almost same, the time to rendering web page through the browser and be able to start interaction. You can measure this performance easily with Lighthouse, this is popular chrome browser extension, as the first step, you should check the metrics, it called "First Content Paint".

---

### #14
This is an example of result page, in the area enclosed by red border, you can see that metrics. "First Content Paint" is the time from when the page starts loading to when any part of the page's content is rendered on the screen. This is an important metrics, because if this time is long, it means initial downloaded resources were huge due to stylesheet or JavaScript or some external resources or something. In addition, it is not enough to improve First Content Paint, you have to take care of the metrics called "Time to Interactive" as well, this is the time it takes for your page to become **fully** interactive. This means that not only the content is **fully** visible, but also, all page event handlers have already been registered for the visible content.

---

### #15
If you selected the Blazor Server, you don't have to care about this performance, Blazor Server has an advantage in Load Time Performance. On the other hand, if you selected the Blazor Web Assembly, initial downloaded file size tends to be huge, I'm not going to tell you in detail in this session, but I'm going to introduce several ways how to reduce the initial loading file size with Blazor Web Assembly. First, you can use Brotli to compress files over HTTP, please note you can do that even if your server doesn't support Brotli by writing some code in you project, one of the test results shows reduced file size is around 80%.

Second, turn IL trimming function on, the function can remove unused source code from assembly, test result shows 44% file size decreasing. 

Thirdly, installing a wasm-tools to your project, this is easy to use, however a little bit improvement like 7%. 

Lastly, If it possible, you can cut the capability of the globalization and Time Zone, this will be effective like 37% file size decreasing. I attached links to official documentation in this slide, if you are interested in the detail, you can refer it later.

I haven't written down in this slide, but Pre-rendering technique is also doable for Web Assembly to improve a Load Time Performance. As you can see, many performance improvement methods are already available.

---

### #16
Second point is Run Time Performance, this is about how responsive the web app is to user interactions, please imagine about application's interactions are slow, for example, response time to button clicks is slow, your keystrokes are reflected to screen little later, too heavy to navigate a page or scrolling, these problems will occur frustration. So, this is also important point.

---

### #17
Chrome developer tools is good solution to identify performance bottlenecks, let's say the memory leak seems to be happened in your web application, you can use the memory profiler provided by the dev tools, in order to identify memory leaks in the application.

---

### #18
Then, I am showing some guidelines to improve Run Time Performance, first bullet is about a DOM Tree, to improve the performance, you should keep that less than 1.5 thousand nodes in total, the maximum depth is 32, and parent node doesn't have more than 60 child nodes. To following this guideline, it is better way to create DOM node only when needed and destroy them when they are no longer needed. I am going to demonstrate how to archive this way a short time later.

---

### #19
Third point is Soft Performance, this point is not easy to talk, hard to measure, it is necessary to understand UI and UX deeply, so I'm not going to go to the detail in this session but let me give you some examples. How easy it is for your user to find and navigate to the **feature** they want to use. How appealing the look and feel of your application is. How good the error messages your software produces to understand what the end user did wrong. Let me say again this point is not easy, but ultimately, you have to improve this performance as well for your customers.

---

# 4. Tips of web app performance (10min.

### #20
OK, in this topic, I'm going to introduce one of the ways how to improve the Run Time Performance for your Blazor web application. Please remember the guideline of Run Time Performance, if there are lots of DOM nodes in your application, like over 1.5 thousand, it will be an impact to your application. However, we often have to make a page with many elements, for example, like an index page to show all of records overall.

Of cause, you can consider about **splitting** their records to small portion, like a hundred items on each page and navigate with pagination. But with this approach, the user has to click paging link again and again to reach the item they want to see.

---

### #21
So, I am talking about Component **Virtualization** as an alterative way. This is a technique for limiting UI rendering to just the parts that are currently visible. You can use this technique for huge amount of looping content, like list, card, or table. Component **Virtualization** is using a scroll bar to show all of items in single page, and with calculating the position of scroll, just rendering necessary DOM inside a viewable area. Then, when rendered DOM go outside from viewable area, it going to be destroyed. This is an out-of-the-box function for Blazor. So, you can use this so easily.

---

### #22
It is pretty hard to explain with speaking only, so I made an animation to describe, white area is a viewable area, the user only sees this area, gray area is invisible area, it means, the DOM is in invisible area is not necessary, so Component **Virtualization** creates the DOM node if it turns to visible and delete it if it turns to invisible.

---

### #23
How to write a code for **Virtualization** in Blazor, this is so simple, let's say about creating the table element, with the regular way, we use foreach to create each row inside a table. As you can see the bottom of sample code, you can use **Virtualize** component instead of using foreach, I add some property in **Virtualize** component, Items property needs to be assigned whole data you want to show, and I declare the item with Context property, so I can use Item Context to show each data in a single row like foreach looping.

---

### #24
So, let's take a look at the results, firstly, I am showing a result of **non-virtualized** table with ten thousand of items, as you can see, the application was crashed due to the out of memory.

---

### #25
So I tried to reduce the number of items to 2.5 thousand, somehow the page can be shown, but I was scrolling items inside a table, be crushed too.

---

### #26
Finally, I am showing the result of **virtualization**

---

### #27
As you can see, the page can show the table instantly, and it is okay to show items even if I scrolled anywhere. 

---

### #28
This is a changing of HTML DOM Elements by checking Chrome developer tools, you can confirm that elements are going to be **re-written** following to the position of scroll. This is exactly easy to use to improve the performance, if you have lots of looping element in your application, let's try it right after this session.

---

# 5. You need more complex functional UI? (5min.

### #29
Fortunately, we could make **virtualized** table with good performance however, you can imagine your client requests additional functions to this table, the function is like sorting or filtering or something like that, can you do that? Maybe you would be able to implement these functions, but after finishing the implementation, you have to think about the performance again.

---

### #30
In Japan, many developers face performance issue after implementing complex functions. To keep both functionality and performance is so difficult. Furthermore, I'd like you to remember third performance point called Soft Performance, with the complex UI, it is too hard to navigate the end user to each **feature**, easily produce bad user experience. This is one of the reason why many businesses use application have bad user experience.

---

### #31
If the complex and high functional UI is required, I recommend you consider using third party UI components, this is our representative grid control, called IgGrid.  We are reseaching User Experience over decades, as a result, User-Centered design applying to this grid, it means you don't need to care about Soft Performance anymore, additionaly, a lot of **features** implemented like sorting, filtering, grouping, pinning, exporting, changing layout and so on, you can turn on or off for each **feature** easily, and also, our grid knows as fastest grid in the market. Please keep in mind you can be released from stressfull UI/UX things by using our controls, and you can concentrate to the scope that you really should focus to.

---

# 6. What we have done to customer in Japan. (2min.

### #32
I'd like to show you what we've done to customer who is interested in Blazor in Japan, we support developers with several ways, for example, supported them to adopt Blazor as brand-new framework as like to convince their manager to decide to select Blazor, also we provided the training video to learn Blazor for beginner.  Solved their UI requirements trough our controls. If they want to more dedicated support, we provided them consultation service like a code-reviewing or something. As a result, the customer could start Blazor project without any anxiety.

---

# 7. Takeaway (1min.

### #33
Through this session, there are three takeaways I wanted to tell. If you hesitate to try to Blazor, no worries, let's begin it from today.
For develop web application, you should care about three kinds of points for a good performance.
If more complex UI is required, you can rely on the professional like Infragistics, we love to support developers.
That's all for my session, thank you for listening! Thanks DotNetDev community! チョンマル  カムサハムニダ！
