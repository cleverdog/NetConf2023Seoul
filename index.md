---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
marp: true
# size: 4:3
---

![bg 100% right:36%](./e716d7b23c2c510c2ce94363b05ab74a.gif)

# **.NET Conf 2023 <br>x Seoul**

Let's start developing Blazor applications with "high performance" tuning!

---

# 자기소개

**Motoki Nakae**

![bg 90% right:30%](./b65b1eb0079f5b1b925b6d3da53c0fe3.jpg)

Solutions Consultant at Infragistics.
I am solving customers’ UI/UX problems with our knowledge and products, especially about web applications every day.
Also known as a "dog lover".

![width:40](./Circle-icons-mail.svg.png) <small>MNakae@infragistics.com</small>, <small>ESEA@infragistics.com</small>
![width:40](./Twitter_Social_Icon_Circle_Color.png.twimg.1920.png) <small>@Kashikoinu</small>

<style scoped>
* {
    vertical-align:middle
}
</style>

---

<div style="text-align:center; margin:0; line-height:1">

![width:1100](./persons.jpg)

</div>

<div style="display:flex; width:102%; justify-content: space-around; text-align:center; margin-top:-50px; margin-left: -2.4%">

<div>

### Ken Azuma

CEO at Infragstics JAPAN

</div>

<div>

### Dongsu Jo

Sales Manager, ESEA

</div>

</div>

---

# Infragistics

<div style="text-align:center">

![width:1000](./sampleapps.png)

</div>
We Infragistics provides well designed and high functional UI controls and components for developers over 30 years.

---

![bg contain 75%](./clients.jpg)

---

# <!-- fit -->246
<style scoped>
* {
    text-align:center
}
</style>

---

![bg contain 100%](./chart.png)

---

# What's happening in Japan

<small>

## Demand of Blazor was much increased 2022

</small>

One of common scenario:

- The developer works for implementing desktop application for the system inside a plant.
- They are facing new request that about monitoring system to see a status of plant operation for managers.
- Since the manager have to move around a lot during the job, they want a web application to access from anywhere.
- Performance is important.

<style scoped>
li {
    font-size:90%;
}
</style>

---

# Today's Topics

- The reason why I recommend you Blazor as the web development framework.
- The points you should take care for web application as performance perspective.
- Let's start to create a new Blazor web application with performance tuning.
- What if more complex functional UI components are needed.

---

# Why you should choice Blazor

- You are C# developer.
- You are familiar with Blazor Server.
- You can create latest SPA web application.
- Document and showcase are incresing day by day.
- Microsoft is paying a lot of attention to Blazor.
- A lot of library vendors were adopted Blazor including Infragistics.

---

# Time to start Blazor!

![bg right:40% 80%](./ue_mezasu_man.png)

<style scoped>
h1 {
    text-align:center;
    padding-top:3.95em;
}
</style>

---

# <!-- fit -->Web application performance
<style scoped>
* {
    text-align:center;
    padding-top:3.75em;
}
</style>

---

# <!-- fit -->Three dimensions of web app performance

<small>

## 1. Load Time Performance

</small>

- How fast the web application load.
- For a desktop app, the time to excute application and be able to start interaction for user.
- To measure this performance, I suggest your use the Lighthouse.
- You should check "First Contentful Paint" metrics firstly.

---

![](./47a0ea1c7a9947cc06d0b2b3061b44c6.png)
<style scoped>
* {
    text-align:center;
    vertical-align:center;
    padding-top:14px;
}
</style>
---

# To reduce the Load Time

<table>
    <thead>
        <tr>
            <th></th>
            <th>Tips</th>
            <th>Sample Result</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>Blazor Server</th>
            <td>Basically, you don't have to care.</td>
            <td>-</td>
        </tr>
        <tr>
            <th rowspan="4">Blazor WebAssembly</th>
            <td>Use Brotli to compress files.(<a href="https://learn.microsoft.com/en-us/aspnet/core/blazor/host-and-deploy/webassembly?view=aspnetcore-7.0#customize-how-boot-resources-are-loaded">document</a>)</td>
            <td>80%</td>
        </tr>
        <tr>
            <td>Turn on IL trimming to reduce the size of published output.(<a href="https://learn.microsoft.com/en-us/aspnet/core/blazor/host-and-deploy/configure-trimmer?view=aspnetcore-7.0">document</a>)</td>
            <td>44%</td>
        </tr>
        <tr>
            <td>Installing a wasm-tools.(<a href="https://devblogs.microsoft.com/dotnet/asp-net-core-updates-in-net-6-rc-2/#native-dependencies-support-for-blazor-webassembly-apps">document</a>)</td>
            <td>7%</td>
        </tr>
        <tr>
            <td>If possible, cut the globalization and TimeZone capability.(document <a href="https://learn.microsoft.com/en-us/aspnet/core/blazor/performance?view=aspnetcore-7.0#minimize-app-download-size">1</a> / <a href="https://learn.microsoft.com/en-us/dotnet/core/runtime-config/globalization">2</a>)</td>
            <td>37%</td>
        </tr>
    </tbody>
</table>

<style scoped>
table {
    font-size:30px;
}
</style>

---

# <!-- fit -->Three dimensions of web app performance

<small>

## 2. Run Time Performance

</small>

- How responsive the web app is to user interactions.
- Chrome developer tools is good to identify performance bottlenecks.
- Some guidelines to improve run time performance:

    - Less than 1500 nodes in total. The maximum depth is 32 nodes. No parent node has more than 60 child nodes.
    - Properly size images, and lazy load images.

---

# Chrome developer tools

<div style="text-align:center">

![width:1180](./devtools.webp)

</div>

<style scoped>
div {
    text-align:center;
}
</style>

---

# <!-- fit -->Three dimensions of web app performance

<small>

## 2. Run Time Performance

</small>

- How responsive the web app is to user interactions.
- Chrome developer tools is good to identify performance bottlenecks.
- Some guidelines to improve run time performance:

    - Less than 1500 nodes in total. The maximum depth is 32 nodes. No parent node has more than 60 child nodes.
    - Properly size images, and lazy load images.

---

# <!-- fit -->Three dimensions of web app performance

<small>

## 3. Soft Performance

</small>

This dimension is not easy to talk, hard to measure, this is related to User Experience for example:

- How easy it is for your user to find and navigate to the feature they want to use.
- How appealing the look and feel of your application is.
- How good the error messages your software produces to understand what the end user did wrong.

---

# <!-- fit -->Tips of Web application performance
<style scoped>
* {
    text-align:center;
    padding-top:3.75em;
}
</style>

---

# Component Virtualization

Virtualization is a technique for limiting UI rendering to just the parts that are currently visible.

- You can use this technique for huge amount of looping content, like list, card, table.
- With calculating the position of scroll, just rendering necessary DOM inside a viewable area.
- When rendered DOM go outside from viewable area, it going to be destroyed.
- This is an out-of-the-box function for Blazor.

---

![bg](./5b6a72b8d79900b9d0f7b955d408d0ba.gif)

---

# <!-- fit -->Let's make virtulized table with 10k items

```html
<table>
    ...
        @foreach (var item in Items)
            <tr>
                <td>@item.FirstName</td>
                <td>@item.LastName</td>
                ...
        }
```

```html
...
        <Virtualize Items="@Items" Context="item">
            <tr>
                <td>@item.FirstName</td>
                <td>@item.LastName</td>
                ...
        </Virtualize>
```

<style scoped>
code {
    font-size: 60%;
}
</style>

---

# What happens if you don't virtulize?

<small>

## With 10k items

</small>

<div>

![width:800px](./2aa8ea9d510a13cf32991e6910ab4ad1.png)

</div>

<style scoped>
div {
    text-align:center;
}
</style>

---

<small>

## With 2.5k items

</small>

![bg](./bb2ac9b2c2c0b20ad56cc0666d9b232c.gif)

<style scoped>
h2 {
    color:#fff;
    background: rgba(0,0,0,.5);
    display: inline-block;
    padding: .3em
}
</style>

---

# Let's look at the result of virtulization
<style scoped>
* {
    text-align:center;
    padding-top:3.75em;
}
</style>

---

![bg](./efc5c6f2d345297a047defca54d94491.gif)

---

![bg](./c7b7f9457c230b0ec2cd37f89952e597.gif)

---

# <!-- fit -->You need more complex functional UI?
<style scoped>
* {
    text-align:center;
    padding-top:3.75em;
}
</style>

---

# To keep both functionality and performance is so difficult

- Feature request that never ends.

    - Sorting, Filtering, To register the short cut and so on.

- The difficulty of performance tuning increase for functional UI cotrols.
- Too hard to navigate the end user to each feature, easily produce bad user experience.

---

![bg 95%](./4c95855a5be3aa6fa0a106b2d524cb3e.gif)

<!--
_backgroundColor: #202020
-->

---

# What we have done for customer in Japan.

- Supported them to adopt Blazor as blandnew framework.
- Provided the training video to learn Blazor for biginner.
- Solved their UI requirements trough our controls.
- Provided consultation service.

![bg right:30% 100%](./internet_school_e-learning_man.png)

---

# Takeaway

<style scoped>
div {
    font-size: 120%;
    line-height:1.6
}
li {
    margin-bottom:1em
}
</style>

<div>

- You don't need to hesitate to Blazor now, let's try to start!
- Handle three kind of dimensions for performance!
- If complex UI is require, rely on professional like Infragistics!

</div>
