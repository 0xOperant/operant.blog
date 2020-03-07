---
title: "Tribe of Hackers Red Team: Tribal Knowledge from the Best in Offensive Cybersecurity"
date: 2020-03-05T21:13:39-05:00
draft: false
description: "Sharing my \"Tribe of Hackers Red Team: Tribal Knowledge from the Best in Offensive Cybersecurity\" book input"
tags: ["tribe of hackers","red team","book","writing"]
featured_image:
author: "@operant"
---

{{< figure src="/images/ToH.jpg" style="width:100%" >}}

Last year I had the honor of being asked to contribute to the "Tribe of Hackers Red Team: Tribal Knowledge from the Best in Offensive Cybersecurity" book by Marcus J. Carey and Jennifer Jin. They were passed my contact info by my colleagues leading other large internal corporate Red Teams, and I'll admit I was blown away. They were on a tight deadline at the time, and wanted my input quickly. I was overseas at a conference, and literally tapped this out on my tablet on the flight home. With the magic of editing, I think it turned out ok. I've included my input below. Let me know what you think!

> There's no "right way" to become a Red Team member.

## Questions

1. How did you get your start on a red team?

I got my start back in 2006 with the U.S. Navy Red Team, as a contractor. I had just spent about six months working nights as an IDS analyst with another contracting company, and prior to that I was on active duty in the Navy, mostly in signals intelligence. I spent a lot of time leading up to my separation from the Navy studying for certifications and hacking on home-built networks. That was enough to get me in the door, where the real learning began! I spent 10 years with that team, converted to a Government Civilian, and was the Deputy Director by the time I left. I'm now the Director of the Red Team at GE.

2. What is the best way to get a red team job?

This is a question I am posed quite often, and I still struggle to answer it. There's no "right way" to become a Red Team member. I worked with one really smart guy who at one point drove bulldozers. Having said that, demonstrating the ability to think like an attacker is critical, and can't be taught. We can teach technical skills, but mindset seems to be innate. If someone has the right mindset, generally my advice is to pursue applicable training and certifications, and get involved in Capture the Flag (CTF) events. The certifications tell me that the candidate is committed and will follow through (like college degrees), and the CTF events give me an idea of how they will perform as part of a team. I also suggest starting with other infosec jobs, such as pentesting or incident handling.

3. How can someone gain red team skills without getting in trouble with the law?

This really shouldn't be an issue anymore. There is a lot of training available, both online and in-person. Cloud platforms provide cost-effective learning environments, too...we no longer need to buy old gear from eBay or Craigslist to build a home lab.

4. Why can't we agree on what a red team is?

Coming from the US military Red Team community, I have a pretty strong opinion on the misuse of this and other terms with military roots. It's tempting to blame industry marketing for this, but it really is a community problem. Penetration testing is a distinct and separate discipline from Red Team, and furthermore, there is a significant difference between internal Red Teams and consultant Red Teams. These differences can get quite confusing to customers that just want the best engagement they can get with the budget they have, and this can be taken advantage of by less principled teams.

5. What is one thing the rest of information security doesn't understand about being on a red team? What is the most toxic falsehood you have heard related to red, blue, or purple teams?

Red Team operations can be painfully boring. It's mind-numbing, detailed analytical work, punctuated by moments of sheer elation and adrenaline. Most people only see the highlights in the debriefings, or have misconceptions from Hollywood movies.

6. What is the appropriate point in the maturation of a security program to introduce a formal red team into an organization?

I often tell people that they don't need a Red Team engagement until they *think* they don't need a Red Team engagement. As soon as the organization feels like they understand all of the threats and have a good handle on things, it's time for a good Red Team to challenge those assumptions. And that first report won't be pretty.

7. What has been effective at explaining the value of red teaming to a reluctant or non- technical client, or even to your own organization?

Learning the business! I can't stress this enough. The Red Team has to understand what they are attacking, in the context of the business they are supporting. Showing this understanding will go a long way towards establishing trust and true partnership with the customer.

8. What is the least bang-for-your-buck security control that you see implemented?

Vulnerability scanning. While this is an important security function, I rarely see it done correctly, especially at scale. If an organization is too large to keep an accurate asset inventory, how can they possibly expect to be able to scan all the things?

9. Have you ever recommended not doing a red team and offered something else more suitable, even when a customer asked for one? What have you recommended?

Yes, quite often. I've found that while many customers are asking for a Red Team engagement, they're often really (unknowingly) looking for a web app test, or another form of limited-scope penetration test. In these cases I will facilitate an introduction to another team that can better meet their needs. Some may see this as "losing business," but I see it as building trust.

10. What's the most important or easiest-to-implement control that can prevent you from compromising a system or network? For example, how can we help small and medium businesses who have a smaller budget and staff?

Endpoints rarely need to be able to communicate with each other across the network. Blocking or monitoring this type of traffic should go a long way towards limiting an attacker's lateral movement. Keep in mind that the attacker is after data which will reside in a database, etc. Lateral movement is used to locate and acquire the permissions needed to gain access to this data. Limit that movement as much as possible, and force the attackers to make mistakes.

11. Why do you feel it is critical to stay within the rules of engagement?

Rules of Engagement (ROE) are used to define how the engagement should be conducted, the scope of the engagement, who should be contacted in case of emergency, and clearly delineate any other items of importance. The ROE is the primary safety net for both the Red Team and the customer, so if the Red Team were to deviate from those rules, systems could be damaged or physically unsafe conditions could be created. Accidents can and do happen however, so good ROE will define reporting processes for those incidents and the Red Team will be completely honest about what happened.

12. Tell about a time you were busted on a penetration test (physical, network, social engineering, etc.). How did you handle it?

I've never done a penetration test, but I have been a part of many Red Team engagements, including network exploitation, wireless, and even physical assessments overseas. One of my favorite stories is when my teammate and I got busted trying to convince some military personnel to let us plug in a USB thumb drive. A higher-ranking officer overheard the conversation from the next room, and immediately rushed in to confront us. He was shaking with anger, and informed us that "the Red Team did this to me last year, and you're not going to do it again!" I had no idea what he was talking about, but knew I had two choices: I could either back down and admit I was caught, or I could maintain character and react the same way anyone else in that position would have. I chose the latter, and started shouting back that I didn't appreciate accusations while I was just trying to do my job. He didn't buy it for a second, but I wasn't going to give him the satisfaction. He took us to his security officer, who informed him that our (actually fake) ID cards looked normal to him. While the first officer left the room to retrieve the encryption key for his phone (so he could call "my boss"), I explained to the security officer that we had an authorization letter in the car, and we would just grab that and be right back. Once we got in the car, we still had to get off the base...which was nerve-wracking as well! That evening I discovered that there was a Be-On-Look- Out (BOLO) for me issued by the local host-nation police (no doubt the work of the angry senior officer), so I left the country shortly after. I didn't fully relax until I cleared customs in the US.

13. What is the biggest ethical quandary you experienced while on an assigned objective?

Being asked to "target" specific individuals is always a little creepy. I prefer not to, and will always argue against it. I have no problem targeting specific roles or positions within an organization, however, as long as there is a solid threat model justifying it. One example is that I've been asked to look at the social media profile of executives and their families. Careful controls need to be in place, and permission given, before I will entertain tasks like this.

14. Describe the "team" aspect of red teaming. How do you work together to get the job done, including documentation, reporting, and working with the blue team afterwards?

The ability to function as a cohesive team is often what separates highly effective teams from those that are not. While every team member is important, skilled, and talented, no team member is so highly skilled that they can complete an engagement without the help of their teammates. Similarly, no Red Team operator should ever work on an engagement alone. Either physically or virtually, another operator should be working on the same engagement so they can function as a safety/sanity check for each other.
Detailed documentation is of the utmost importance during Red Team engagements. The customer is paying for the information contained in the report, which is derived from detailed, disciplined logging done during the actual engagement.

15. What is your approach to debriefing and supporting blue teams after an operation is completed?

Debriefs should always be tailored to the audience. Defenders should get in depth technical report outs that walk them through the attack path, from start to finish. Ample time for questions should be scheduled, and the Red Team should be prepared for any follow-up reports for key people that weren't able to attend for some reason. I also encourage the Teams to be available for mini retests or other forms of support to enable defenders to learn from the engagement.
This is a partnership, and the report should reflect that...state facts without ego, and recognize that some people are going to be embarrassed or defensive. Be sure to also give credit where credit is due.

16. If you were to switch to blue team, what would be your first step to better defend against attacks, and if it isn't commonly done already, why do you suppose that's the case?

Prevention is preferred, but detection is a must. My first step would be to understand what data sources were available, and make sure they were accessible to defenders. Many defenders have complained of data overload, but almost every engagement I've ever been a part of had shown some kind of blind spot. The more data available to automation and manual queries, the more likely an attack will be detected.

17. A lot of people complain about writing testing reports and a lot of customers complain about the quality of reports. What is some practical advice on writing a good report?

Stick to the facts, and paint the picture of the attack path. Don't use jargon, and provide references to CVEs or technical guides wherever possible. The report is the product you are providing; it is what the customer is paying for. Nothing else matters, so get this right every time. If there are follow-up questions, answer them promptly and accurately and make note of them for your next report.

18. How do you ensure your program results are valuable to people who need a full narrative and context, instead of a showcase of their weaknesses vs. your skill set?

This will vary with each organization, but a good way to start is to identify who the Red Team's true customers are. Customers are different than stakeholders, and this differentiation becomes important when trying to prioritize engagements and reports. Once the true customers and stakeholders are identified, Red Team leadership should begin to tailor their communications to those individuals. Reports should be at the correct level of detail, and clearly answer the inevitable "so what" question before it is even asked. This requires learning the business, and understanding how the technology your Team has just assessed fits into those processes, and therefore the impact of your Team's actions on the business as a whole. The business is the ultimate customer, and the business does not exist solely to run a CIRT (or a Red Team).

19. How do you recommend security improvements other than pointing out where it's insufficient?

Red Teams are often asked for recommendations for security improvements, but frustratingly, the answer is almost always "it depends." Red Teams provide a snapshot- in-time look at an environment. Red Teams likely have no idea *why* the environment looks the way it does, but almost certainly there were decisions made at some point, for some business reason, to design and build the environment in that particular way. One way to take this into account is for the Red Team to sit down with the teams responsible for implementing fixes, and walk through the attack path from start to finish. This helps the network owners get a peek into the mind of the attacker, and the Red Team to understand what challenges the network owners face. Then, potential mitigations can be brainstormed and table-topped at that moment, resulting in quality recommendations that can actually be implemented. The Red Team can even come back at a later date and re-test the environment to see if the recommended fixes are performing as intended.

20. What non-technical skills or attitudes do you look for when recruiting and interviewing red team members? Or, what is one of the most beneficial non-technical skills you use for red team activities?

When I am talking to candidates, I am looking for positive attitudes and strong internal drive/motivation. Red Teamers will often find themselves neck-deep in mind-numbing analysis, the results of which could determine the success of the engagement. Therefore, it is important that candidates are able to motivate themselves to keep going, not lose sight of the objective, and not complain that they're "not doing cool stuff." Red Team work is usually pretty boring, minus the moments of sheer adrenaline when that shell finally comes back, so candidates need to give the impression that they have the patience and determination to accomplish the mission.

21. What differentiates good red teamers from the pack as far as approaching a problem differently?

Good Red Teamers are able to think, plan, and act like an attacker. This ability is often referred to as the "attacker mindset," but it's more of a lifestyle than something that can just be turned on or off as needed. For example, once a good Red Teamer has been trained and conducted physical engagements, that Red Teamer will habitually and unconsciously "case" every building they enter. They will automatically make note of the position and angle of cameras, security personnel, type and condition of locks on doors and windows, etc...all without thinking about it. The same is true for Red Teamers on the keyboard: they will develop an innate ability to "feel" vulnerabilities, and intuitively understand not only how to exploit them, but whether or not they *should* exploit them in furtherance of their ultimate objectives. This quality is difficult to identify in candidates, and even harder to express in words. However, I have seen good results from having candidates demonstrate their talents in skills challenges during the last stages of the interview process. How a candidate approaches problems in a high- pressure virtual environment tells us quite a bit about whether the "attacker mindset" is fully present, needs developing, or simply doesn't exist within a candidate. Not everyone can think this way, and not everyone is cut out to be on a Red Team, and that's ok. I've seen very smart people struggle with this aspect but then go on to build very successful careers in other aspects of cyber security.

## fin

We Red Team members are an opinionated bunch. [Let me know what you think](https://twitter.com/operant), and [don't forget to order your own copy](https://www.amazon.com/dp/1119643325)! There's tons of great stories, tips, knowledge and opinions from many very smart Red Teamers...some you've heard of, and some you haven't (which is awesome). If you're more of a "blue team" person, I've heard there's an edition coming out soon featuring some of the best blue team folks in the industry, so keep an eye out for that.
