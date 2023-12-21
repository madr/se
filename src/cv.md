---
title: cv
layout: cv.hbs
name: Anders Englöf Ytterström
titles: Frontend Engineer, Full Stack Developer, Web standardista
address: Herrhagsvägen 53, 791 76 Falun, Sweden
email: yttan@fastmail.se
github: madr
website: madr.se
work:
  - employer: PlaymakerAI
    type: Data analytics SaaS 
    date: ⁠Nov 2023–now
    location: Remote position
    position: Full Stack Engineer
    responsibilies:
      - Part of a team consisting of Data scientists and Machine learning experts.
      - DevOps, Backend programming, Frontend engineering.
      - Python, NumPy, Pandas, Scikit-learn, React, MaterialUI

  - employer: Stratsys
    type: Process management platform (SaaS)
    date: ⁠Mar 2022–Oct 2023
    location: Remote position
    position: Senior Frontend Architect
    responsibilies:
      - Part of a team consisting of Frontend architects and UX designers.
      - Responsible for the design system, frontend DX and Microfrontend toolchain and architecture.
      - Writing Web components with full ARIA compability, according to the spec.
      - QA and manual testing with screen readers (NVDA, VoiceOver).

  - employer: Iteam
    type: Technical Innovation agency
    date: ⁠Sep 2021–Mar 2022
    location: Remote position
    position: Full Stack Developer
    responsibilies:
      - All source code are released by a FOSS license.
      - Backend programming in Node.js, TypeScript, Express and Next.js.
      - Frontend development in React, Jotai, Formik, Styleguidist and Figma.
      - Code labs and skill sharing.

  - employer: Kundo
    type: Customer service company (SaaS)
    date: Mar 2017–Sep 2021
    location: Stockholm, Sweden
    position: Full Stack Developer
    responsibilies:
      - T-shaped frontend developer focusing on WCAG 2.0 AA, design and mentoring.
      - "Roles besides development: Team Lead, Tech Lead and Security administrator (briefly)."
      - Backend programming in Django and Phoenix, with RabbitMQ as broker/RPC and Celery as job queue.

  - employer: Adeprimo
    type: Digital Fullservice agency
    date: Oct 2007–Feb 2017
    location: Östersund, Sweden
    position: Systems developer
    responsibilies:
      - "T-shaped Systems developer focusing on frontend and backend web development. Fields: Media, Destination, Tourism."
      - High demand on customer experience and context switching.
      - Distributed, remote-first teams with members located in Vaasa (Finland), Örebro (Sweden) and Östersund (Sweden).
      - Consulting for startups based in Östersund and Åre, Sweden.
      - Polopoly, Python, PHP, Sass, jQuery, Wordpress, SilverStripe, .NET.

  - employer: Pierce
    type: Ecommerce (Motocross, MC and Snowmobile accessories)
    date: Mar–Jul 2015
    location: Åre, Sweden
    position: Web developer
    responsibilies:
      - Development and maintainence for 24mx.se, XLMoto.se och sledstore.se.
      - .NET, C#, Azure.

  - employer: Västsvensk tidningsdistribution (VTD)
    type: Distribution
    date: Jul–Aug 2007
    location: Alingsås, Sweden
    position: Newspaper carrier
    responsibilies:
      - Temporary summer position. Delivering Göteborgs-Posten to 300 households by foot. It rained every night.

  - employer: Moment Marketing
    type: Startup
    date: Sep 2006–Apr 2007
    location: Stockholm, Sweden
    position: Web designer
    responsibilies:
      - Frontend development assistance. Employment by the hour.
education:
  - institution: Media and Communication Science, Mid Sweden University
    date: 2004–2007
    location: Sundsvall, Sweden
    graduation: Degree of Bachelor of Arts (incomplete)
    fields: Web design, Computer science, Computer engineering, Programming (Java, C)

  - institution: Staffanskolan secondary school
    date: 2001–2004
    location: Söderhamn, Sweden
    graduation: Student degree
    fields: Media programme, vocational, media production, graphical communication

skills:
  Programming languages: HTML, CSS (Sass), Python, JavaScript (TypeScript), Elixir, Rust, PHP
  Development process: CI/CD, Automated testing, Mentoring, Mob programming, Pair programming
  Web Backend Frameworks: Django, Flask, Phoenix (LiveView), Express
  Web Frontend: React, Redux, Vue, Svelte, Lit, OOCSS, BEM, Living styleguides
  Build systems: Webpack, Parcel, esbuild
  Content management: Wordpress, Joomla
  Testing: pytest, Jest, Lighthouse, Axe, VoiceOver, Voice Assistant, NVDA, Cypress, WebDriverIO, Web Test Runner
  Deployment: AWS, Docker (Podman), Kubernetes, Ansible, Terraform, Azure DevOps
  "Services & Infrastructure": Nameko, RabbitMQ, Celery, Kibana, Prometheus
  Databases: MySQL, Postgres, Elasticsearch, GraphQL, Influx, Timescale
  Version control: Git, Subversion
  Operating systems: Linux, Mac OS, Windows
  Other skills: Inclusive communication, Accessibility compliance, Technical writing
  Languages: Swedish (native), English (fluent)

projects:
  - name: OneUX Component library
    context: Senior Frontend Architect, Stratsys
    date: "2022-2023"
    responsibilies:
      - Implement a reusable set of components as Web components (Custom element with Shadow DOM).
      - Data-driven state over DOM State.
      - Deployed by the MicroFrontend concept and practices.
      - Fully accessible, with keyboard navigation and mouse gestures, according to the ARIA Authoring Practices guide.
      - E2E/Integration tests in a set of real, headless browsers.
      - Packaged as part of a NPM package and a Design system for internal frontend developers.
      - Atomic Design, Microfrontends, Storybook, Custom Elements, Design Systems, Style Guides, Web Components, Lit, Vue.js, ARIA Authoring Practices guides (APG).

  - name: Slussen FastAPI data adapter, Sveriges Almännytta
    context: Full Stack Developer, Iteam
    date: "Okt–Dec 2021"
    responsibilies:
      - "Turn Allmännyttan FastAPI from blob XML to compact JSON."
      - The adapter was used to create a POC to joyfully report a fault of an rental object.
      - Design sprint together with the stake holders.
      - All code was open sourced.
      - TypeScript, FastAPI, Express, React, MIT.

  - name: SEO-friendly embed of knowledgebase
    context: Full Stack Developer, Kundo
    date: "Mar 2020–Mar 2021"
    responsibilies:
      - Embedded a knowledgebase on any site using a simple embed snippet, whereas the knowledgebase is embedded using fetch().
      - Navigation between guides and text search included, all crawlable by googlebot.
      - SPA-compliance.
      - TypeScript, Jest, Google Search Console.

  - name: Accessibility Statement
    context: Full Stack Developer, Kundo
    date: "Sep–Dec 2019"
    responsibilies:
      - Compliance of the EU Directive on the Accessibility of Public Sector Websites.
      - Axe, W3C validators, Lighthouse, manual accessibility testing.

  - name: Kubernetes migration
    context: Full Stack Developer, Kundo
    date: "Jan 2019–Dec 2020"
    responsibilies:
      - Migrating an AWS production environment (several service-modules in different programming languages, message queues and micro services) to Kubernetes, along with all in-house DevOps tooling.
      - "Goals: keep one command deploys to production, keep Kibana logging, supervision of all services."
      - Terraform, Ansible, Docker, Helm, Prometheus, Kubectl, Minikube.

  - name: Facebook Opengraph client
    context: Full Stack Developer, Kundo
    date: "Sep 2017–Mar 2019"
    responsibilies:
      - "Integrating customer support questions posted on Facebook Pages and Messenger into the Dashboard."
      - "Needed to be done asyncronously to not tamper with API credibility."
      - "Python, Django, MyPy, Protobuf, RabbitMQ, Phoenix Presence+Channels, React + Redux"

  - name: Security & GDPR accountable
    context: Full Stack Developer, Kundo
    date: "Sep 2017–Feb 2019"
    responsibilies:
      - Accountable for several projects to fulfil the GDPR directive up to May 25th, 2018 and onwards.
      - Accountable for security processes and planning for the technical platform.

  - name: Engcon pricelist
    context: Interface Developer, Consultant
    date: Nov 2016–Feb 2017
    responsibilies:
      - Prototyp-driven development of a digital version of a printed pricelist, focusing on effiency and MVP.
      - Vue, Django, Twitter Bootstrap

  - name: Wide Ideas
    context: Full stack Developer, Consultant
    date: "Aug 2011–Feb 2017"
    responsibilies:
      - Development of an idea management platform.
      - Handled DevOps, automation of workflows, development of web interface, and backend programming.
      - PHP, Pligg, Python, Flask, MongoDB, Elastic Search

  - name: Östersundstidningar redesign
    context: Interface Developer
    date: "Mar–May 2011"
    responsibilies:
      - Complete redesign of 3 sites with the same locked (and oldfashioned) HTML.
      - An Object-oriented CSS architecture (OOCSS) was used to create a design system and KSS-powered styleguide utilizing Sass mixins.

  - name: Mktwebb
    context: Interface Developer
    date: "Oct 2007–Aug 2009"
    responsibilies:
      - Shared technical solution for a publication platform for 40 newspapers across Sweden, with Polopoly as CMS.
      - Technological ownership and mentoring others to write JavaScript.
      - All HTML and CSS written in collaboration with backend programmers, UX researchers and designers.

personal:
  Advent of code: Every December since 2016, I challenge myself (and sometimes other collegues) to solve AOC puzzles in a programming language of my choice.
  Tajm.me: As a consultant, time tracking is a crucial part of every day work, and using bad time tracking software sucks. For 5 years, I scratched my own itch. Django, DRF and Web standards at its core. Several experimental client side solutions built with D3, React, Vue, Android, iOS and GTK+. (Archived, 2012–2017)
  "Baslyft, bärs & burgare": "My first Progressive Web App, with support to work fully offline once installed on a device. It's a simple app for logging reps, sets and PB's in the gym, with some nice tools built-in: 1RM calculator and KG-LBS converter. Touch-oriented design patterns, React, Redux, localStorage, ServiceWorker and other nifty Web API:s. (On hold, Sep 2019–)"
  Brütal Legend: A site to track progress of owning vinyl copies os songs licensed in an epic video game. Occasionally used as a real-world example to teach TypeScript, React and Redux concepts to collegues. (On hold)
  Utsökt: A simple bookmarking and read list service, with integration to RSS feeds, Pocket and Slack. Inspired by the old, more minimal version of Instapaper. Elixir, Phoenix LiveViews. (In progress)
  Smed: "A pluggable static site generator, inspired by Metalsmith. The goal is to replace my own sites in Metalsmith, and to learn Rust. (In progress)"
courses:
  - ElixirConf EU, Warshawa (2020, postponed due to the Coronavirus pandemic)
  - Att leda utan att vara chef, Företagsakademin (2019)
  - Modern React with Redux, Udemy (2017)
  - Ethical Programming from Scratch, Udemy (2018)
  - Android Developer Nanodegree, Udacity (2017)
  - PyConf, Stockholm (2017)
  - Nordic.JS, Stockholm (2014)
  - TiConf, Amsterdam (2014)
  - FFConf, Brighton (2012)
  - DevSum, Stockholm (2012)
  - Certificed Scrum Master Course, Crisp AB (2010)
---

**Anders Ytterström**, Web Developer with 16 years of passion. I strive to constantly come up with new ways of improving both products and processes for all participants in projects I am part of.

I prefer my coffee black, just like my metal, and preferably drip brewed by hand.

I also aim to be a [roadie, not a rockstar](https://www.linkedin.com/pulse/20140816105034-167544180-you-don-t-want-a-rock-star), as well as defending [boring tech](https://mcfunley.com/choose-boring-technology).
