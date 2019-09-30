# Mevi!
> **Note:** This is project for education purpose only.

# What's the idea ?
Mevo is bike rent app working in Tricity and other cities in Poland. While ago they removed option of reservation bike for 15 min before rent. I was curious if there is any way to do it using some programming skills. If not I will propably make some projects out of it. Here I want to provide my thought pattern and process.



# Process

 1. **Introduction**

App looks like this. It connects to a server sends and receive data. Like most of apps do.

![https://i.imgur.com/R03dhHi.png](https://i.imgur.com/R03dhHi.png)

Within a little bit of research I found out that in order to check traffic on my phone I need to root my phone. Bad idea because it is still on warranty.

2. **Proxy**

Here comes Fiddler 

>“Fiddler is a free web debugging tool which logs all HTTP(S) traffic between your computer and the Internet”

Looks like perfect solution isn’t it?. Let’s check it.
![](https://i.imgur.com/TG47RDB.png)
This is what I get when im trying to log in. And pop-out in app saying “Log in failed”.
All because … quick research.
![](https://i.imgur.com/LLJ3Qzo.png)

All of these are moving us to next step.

3.  **Manifesto**

We need to make simple changes in app in order to see http traffic from the app.
After downloading the .apk itself and tool called Apktool work goes on.
[Apktool](https://ibotpeaches.github.io/Apktool/) allow us to do many things, one im interested in is to decompile apk.
After decompiling we have access to AndroidManifest.xml in which we can see that Mevo is using firebase but that’s not the thing now.
After changing network security config I should be able to see request and endpoints.
Compiling it back in .
![](https://i.imgur.com/zEfZQkX.png)

3. **Errors and more errors**

>Parse error
>
>“There was a problem while parsing the package” 

 I guess we are missing one step and this is with a gentle research Signing the App. Fastest way:

https://github.com/patrickfav/uber-apk-signer

![](https://i.imgur.com/0g2lu8l.png)

4. **Installing and results**

After installation I am able to see what's going in and out.
![](https://i.imgur.com/DRhEwmx.png)
That's a mile stone but very small. 

Now we have endpoints so let's test it manually with required parametres.
REQ POST /api/login
![](https://i.imgur.com/df0F4SK.png)


RESPONSE

![](https://i.imgur.com/72wW8Lm.png)

Basic stuff, by the time I uploaded this they have updated Mevo with 5 min reservation feature which can be unlimited ( ͡º ͜ʖ͡º) to be continued ...
