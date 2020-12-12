---
layout: post
title: What data engineers actually do, part 1
---

Beyond the well-understood problems of no data and dirty/fragmented/unusable data, companies without data engineers usually suffer from two things:

Data silos: There's data, and probably a lot of it, but most data sources aren't connected and have no access to each other. Large stores of data exist in a contextless vacuum, inaccessible or largely useless to anyone who might want or need to make use of them. As far as these struggling companies are concerned, data exists in relation to other data. It needs to be connected to other data to be useful. Data users need to be able to access multiple data sources at a time. 

Ad hoc data analysis: This is a direct result of the previous problem. Data analysts (scientists, engineers, decision-makers) don't have the ability to work with others in their company. They can't easily share their insights or applications with each other. They might be forced to build temporary or unscalable data pipelines and workflows for themselves or their teams that no one else in the company can access or contribute to. They might be frustrating themselves building dashboards that no one else ever looks at. They might not even have the ability to get large-scale views of their data because the infrastructure for that doesn't exist yet.


