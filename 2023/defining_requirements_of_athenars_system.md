> It's important to think about your entire system and spend time planning and designing before building. Learn about the underlying requirements behind the Athenars system design.

Firstly, what is an Athenars system? It's a comprehensive cohesive system that integrates modern cloud technologies and building automation in a data driven way, all locally on premises. We want this system to be well designed, considered and as thoughtful as possible.

> Time spent planning a system before building it is seldom wasted.

Being deliberate in system design means not buying in to a small part of a complete system without considering the whole first. Going in early first then seeking to add onto it and integrate other pieces later is a well trodden path to frustration and needing to do things twice. Or three times.

# What's the philosphy behind the design?

The underlying philosophy of the Athenars approach will drive our system design. These principles may not align with you, or they may. But it is important to consider your overall approach before you start building. Here is a high level list of our requirements that are important to the Athenars approach.

  - the system should be privacy preserving.
  -  the system should be well integrated and able to be extended in the future.
  - the system should be based on open source, open protocols and open standards.
  - the system should perform well, with low latency.
  - the system should be reliable and fault tolerant.
  - the system should be modular and loosely coupled with as little centralisation as possible.
  - the system will likely be primarily event-driven, so system design decisions should consider this over more batch process oriented approaches.
  - the system infrastructure (and data) should be local only, on premises, self hosted.
  - the system should provide good data observability from a wide range of data sources.
  - vendor lock-in and proprietary solutions should be avoided.

You should now know if the Athenars approach sounds appealing to you.

# Decisions, decisions

In considering options, we need to be mindful and consider the most cutting edge or proven cloud technologies that are open source and can be self hosted, while also avoiding unnecessary complexity. There is a balance to be found here.

**We need to consider that popularity is not necessarily the only indicator of quality or suitability**. Some options are popular and are well suited to certain use cases, that are not well aligned with our Athenars wants / needs. Some popular options come with an element of lock-in or limitation or dependency or complexity which we want to avoid.

**We want to avoid single points of failure** as far as is reasonably practical. This will be a key theme throughout our system design. We want to remove those single points of failure but not where we get close to diminishing returns, increased cost, increased complexity and increased size.

**We want good performance, but we don't want to be wasteful**. We want a good balance of performance and energy efficiency. With that, comes the consideration of price as newer and more costly hardware tends to be better performing and more energy efficient.

**We want uptime**. While system downtime at home may not have the same explicit financial costs as downtime in a commercial setting, we take uptime more seriously than many. Our data is important. Our systems at home are important. We don't casually feel that system failures are ok at home because they do not have the same explicit and direct costs as to a business. And with more people working from home or running businesses from home, uptime will only become more important.

**We want quality at home**. We are unconstrained by business needs or large workforce needs. We don't need to choose systems based on what most of the workforce already uses. We can be more agile and adaptive and select the specific quality options we want.

# Who do you want to associate with?

Understanding vendor ethics and business models and practises should be considered. Does a company tend to err more towards user hostile actions? Is there significant VC investment that will aim to squeeze as much revenue out as possible? Is a company moving towards cloud-centric data collection? Is a company collecting user telemetry in ways that are user hostile and untrustworthy?

A lot of our system needs and requirements are mutually supporting. There are many options are ways we could go. None would necessarily be wrong. As long as a system is designed in a holistic and considered manner to a users requirements, it will be a success.

The Athenars system design is specific to our requirements and wants and needs stated above. Considerable time and consideration has gone into designing the Athenars system.

Additional more detailed Athenars system design thinking is explained in the following posts.
