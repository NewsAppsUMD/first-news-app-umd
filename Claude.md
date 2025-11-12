# Interactive First News App Tutorial with Claude

Welcome to an interactive tutorial for building your first news application! This tutorial will guide you through creating a web application that displays Baltimore 911 overdose call data on an interactive map.

## How This Tutorial Works

This is an **interactive tutorial** designed for use with **Claude Code in GitHub Codespaces**. Unlike traditional tutorials where you copy and paste code, you'll:

1. **Describe your goals** - Tell Claude what you want to accomplish
2. **Answer questions** - Claude will check your understanding of key concepts
3. **Get implementations** - Claude will write and explain the code for you
4. **Learn by doing** - You'll understand the "why" behind each step

## Prerequisites

- A GitHub account
- GitHub Codespace with Claude Code running (you're probably already here!)
- Basic familiarity with web concepts (HTML, URLs, etc.)

## What You'll Build

By the end of this tutorial, you'll have created an interactive web application featuring:
- A data-driven Flask web application
- An interactive map showing 911 overdose call locations
- Detail pages for each incident
- A responsive design that works on mobile devices
- A published site on GitHub Pages

**Example:** https://newsappsumd.github.io/first-news-app-dwillis/build/index.html

---

## Act 1: Hello Codespaces & Git

**Goal:** Get comfortable with your development environment and version control.

### Step 1.1: Understanding Your Environment

Before we start coding, let's make sure you understand where you are:

**Question for you:** Can you describe what a GitHub Codespace is and why it's useful for development?

<details>
<summary>Click to see explanation</summary>

A GitHub Codespace is a cloud-based development environment that runs in your browser. It provides:
- A pre-configured Linux environment
- All the tools you need (Python, git, editors)
- Access from anywhere
- No local setup required

This means you can develop without installing anything on your computer!
</details>

### Step 1.2: Your First Git Commit

**Task:** Tell Claude:
> "I want to edit the README.md file to personalize it with my name, then commit the change to git."

**Before Claude implements this, answer:**
- What does `git commit` do?
- Why is version control important for projects?

**After implementation, Claude will explain:**
- How the file was modified
- What the git commands do
- Why we write meaningful commit messages

---

## Act 2: Hello Flask

**Goal:** Understand web frameworks and create your first Flask application.

### Step 2.1: Understanding Web Frameworks

**Question for you:** Before we install Flask, can you explain in your own words:
- What is a web framework?
- What problem does Flask solve?
- What does "routing" mean in web development?

<details>
<summary>Click to see explanation</summary>

A **web framework** like Flask handles the complex parts of web development:
- Routing URLs to specific functions
- Rendering HTML templates with data
- Handling HTTP requests and responses

Without a framework, you'd have to write all this infrastructure yourself!

**Routing** is the process of mapping URLs (like `/` or `/about`) to specific functions that generate the page content.
</details>

### Step 2.2: Setting Up Flask with uv

**Task:** Tell Claude:
> "I want to set up Flask using uv as my package manager. Please create a virtual environment and install Flask."

**Understanding check:** After Claude installs Flask, explain:
- Why do we use a package manager like uv?
- What is a virtual environment?
- Why not just install packages globally?

### Step 2.3: Your First Flask App

**Task:** Tell Claude:
> "I want to create a basic Flask application in app.py that displays 'Hello World' when I visit the root URL."

**Before implementation, answer:**
- What file will contain our Flask application?
- What does the `@app.route()` decorator do?
- What is `localhost:5000`?

**After implementation, Claude will:**
- Create `app.py` with the basic Flask structure
- Explain each part of the code
- Show you how to run the server
- Explain what `debug=True` does

### Step 2.4: Creating Templates

**Task:** Tell Claude:
> "I want to create a templates directory and an index.html template that Flask will render."

**Understanding check:**
- Why does Flask look for templates in a specific directory?
- What's the difference between static HTML and a template?
- What is Jinja and what does it do?

---

## Act 3: Hello Data

**Goal:** Learn to work with CSV data and display it dynamically.

### Step 3.1: Understanding the Data

**Task:** Tell Claude:
> "I want to download the Baltimore 911 overdose data CSV and save it to a static directory."

**Before implementation, answer:**
- What is CSV format?
- Why is CSV commonly used for data journalism?
- What kind of information do you think this dataset contains?

**After implementation, Claude will:**
- Create the static directory
- Download the data file
- Show you the structure of the data
- Explain the columns in the dataset

### Step 3.2: Reading CSV Data

**Task:** Tell Claude:
> "I want to create a function that reads the CSV file and returns it as a list of dictionaries."

**Understanding check:**
- What is a dictionary in Python?
- Why is DictReader better than just reading lines?
- Why do we convert the CSV object to a list?

**After implementation, Claude will explain:**
- How `csv.DictReader` works
- Why we open files with context managers
- How to access data from dictionaries

### Step 3.3: Displaying Data in a Table

**Task:** Tell Claude:
> "I want to pass the CSV data to my template and display it in an HTML table."

**Before implementation, answer:**
- How do we pass data from Flask to a template?
- What Jinja syntax do we use for loops?
- How do we access dictionary values in Jinja?

**After implementation, Claude will:**
- Modify `app.py` to pass data to the template
- Create an HTML table in the template
- Explain Jinja's template syntax
- Show you how to access specific fields

---

## Act 4: Hello Detail Pages

**Goal:** Create individual pages for each data record using dynamic routing.

### Step 4.1: Understanding Dynamic Routes

**Question for you:**
- What is a dynamic route?
- How is `/user/123/` different from `/about/`?
- What is a URL parameter?

<details>
<summary>Click to see explanation</summary>

A **dynamic route** contains variable parts. For example:
- `/call/P221761572/` - specific call ID
- `/call/<call_number>/` - template that matches any call ID

The `<call_number>` part is a **URL parameter** that gets passed to your function, allowing one route to handle many different URLs.
</details>

### Step 4.2: Creating Detail Route

**Task:** Tell Claude:
> "I want to create a detail route that accepts a call_number parameter and displays a detail page for that specific 911 call."

**Understanding check:**
- How does Flask extract parameters from URLs?
- What happens if someone visits a call_number that doesn't exist?
- Why do we need to loop through the data to find the matching record?

**After implementation, Claude will:**
- Add the detail route to `app.py`
- Create the detail.html template
- Explain how URL parameters work
- Show how to handle 404 errors with `abort()`

### Step 4.3: Linking Pages Together

**Task:** Tell Claude:
> "I want to add hyperlinks to the index table so users can click to see each call's detail page."

**Understanding check:**
- How do we construct URLs in Jinja templates?
- What makes a good user experience for navigation?
- Why is it important to make data explorable?

---

## Act 5: Hello JavaScript & Maps

**Goal:** Add interactive maps using Leaflet.js to visualize geographic data.

### Step 5.1: Understanding Web Maps

**Question for you:**
- What is a JavaScript library?
- Why would we use Leaflet instead of Google Maps?
- What are latitude and longitude?

<details>
<summary>Click to see explanation</summary>

**JavaScript libraries** like Leaflet provide pre-written code for common tasks. Leaflet is:
- Open source and free
- Lightweight and fast
- Customizable with different map tiles

**Lat/long coordinates** are how we specify locations on Earth:
- Latitude: -90 (South Pole) to +90 (North Pole)
- Longitude: -180 to +180 (wraps around Earth)
</details>

### Step 5.2: Adding a Map to Detail Pages

**Task:** Tell Claude:
> "I want to add an interactive Leaflet map to each detail page showing the location of that specific 911 call."

**Understanding check:**
- How does JavaScript interact with HTML?
- What is the purpose of the map div element?
- How do we pass data from Flask/Jinja to JavaScript?

**After implementation, Claude will:**
- Add Leaflet CSS and JS to the template
- Create a map div
- Write JavaScript to initialize the map
- Explain how map coordinates are used
- Show how to add markers

### Step 5.3: Creating an Index Map

**Task:** Tell Claude:
> "I want to create a map on the index page that shows all 911 calls at once with clickable markers."

**Understanding check:**
- What is GeoJSON and why is it useful?
- How do we loop through data in Jinja to generate JavaScript?
- What makes a marker clickable?

**After implementation, Claude will:**
- Create a GeoJSON feature collection
- Explain the GeoJSON format
- Add popups to markers
- Create links from map markers to detail pages

---

## Act 6: Hello CSS & Design

**Goal:** Make your application look professional and work well on mobile devices.

### Step 6.1: Understanding Web Design

**Question for you:**
- What is CSS and what does it control?
- What is responsive design?
- Why is mobile-friendly design important?

<details>
<summary>Click to see explanation</summary>

**CSS (Cascading Style Sheets)** controls the visual presentation:
- Colors, fonts, spacing
- Layout and positioning
- Responsive behavior

**Responsive design** means your site adapts to different screen sizes, from phones to large desktop monitors, providing a good experience on all devices.
</details>

### Step 6.2: Adding Basic Styles

**Task:** Tell Claude:
> "I want to create a stylesheet and add professional styling to my index page including a navigation bar, better typography, and improved table design."

**Understanding check:**
- How do we link a CSS file to an HTML page?
- What does `url_for('static', filename='...')` do?
- Why do we put CSS in a separate file?

**After implementation, Claude will:**
- Create style.css
- Add navigation and header styling
- Style the table
- Explain CSS selectors and properties
- Show how Flask serves static files

### Step 6.3: Making It Responsive

**Task:** Tell Claude:
> "I want to add media queries to make my application responsive, hiding less important table columns on smaller screens."

**Understanding check:**
- What is a media query?
- Why hide columns instead of making them smaller?
- What is mobile-first design?

**After implementation, Claude will:**
- Add viewport meta tag
- Create media queries for different screen sizes
- Explain breakpoints
- Show how to test responsive design

### Step 6.4: Custom Map Markers

**Task:** Tell Claude:
> "I want to replace the default Leaflet markers with custom icons to make the map more polished."

**Understanding check:**
- Why customize markers?
- How do we serve image files in Flask?
- What are icon sizes and why do they matter?

---

## Act 7: Hello Internet (Publishing)

**Goal:** Freeze your Flask app into static files and publish to GitHub Pages.

### Step 7.1: Understanding Static vs Dynamic

**Question for you:**
- What's the difference between a dynamic Flask app and static HTML files?
- Why would we want to publish static files instead of running Flask on a server?
- What are the advantages and limitations of static sites?

<details>
<summary>Click to see explanation</summary>

**Dynamic sites** (Flask running):
- Generate pages on each request
- Can handle user accounts, forms, databases
- Require a server running Python

**Static sites** (frozen):
- Pre-generated HTML files
- Fast and cheap to host
- Can't handle user input or change without rebuilding
- Perfect for data journalism projects that don't need interactivity

**Frozen-Flask** converts your dynamic Flask app into static files, taking the best of both worlds: easy development with Flask, cheap/fast hosting with static files.
</details>

### Step 7.2: Installing and Configuring Frozen-Flask

**Task:** Tell Claude:
> "I want to install Frozen-Flask using uv and create a freeze.py script that will generate static files for all my pages."

**Understanding check:**
- Why do we need to register a generator for detail pages?
- What does the build directory contain?
- How does Frozen-Flask know which pages to create?

**After implementation, Claude will:**
- Install Frozen-Flask
- Create freeze.py
- Explain how URL generators work
- Show the build directory structure
- Test the frozen site locally

### Step 7.3: Publishing to GitHub Pages

**Task:** Tell Claude:
> "I want to publish my frozen site to GitHub Pages so anyone can see it on the internet."

**Understanding check:**
- What is GitHub Pages?
- Why do we use a separate branch (gh-pages)?
- What is the URL pattern for GitHub Pages?

**After implementation, Claude will:**
- Configure app for frozen URLs
- Create and push to gh-pages branch
- Explain the GitHub Pages publishing process
- Provide your live URL
- Explain how to update the site

---

## Act 8: Understanding & Extending

**Goal:** Solidify your knowledge and explore ways to extend the application.

### Step 8.1: Review Key Concepts

Take a moment to reflect. Can you explain these concepts in your own words?

1. **MVC Pattern**: How does Flask separate data (Model), presentation (View), and logic (Controller)?
2. **Templating**: How does Jinja combine data with HTML?
3. **Routing**: How do URLs map to functions?
4. **Static vs Dynamic**: When would you use each approach?
5. **Responsive Design**: How do media queries work?

### Step 8.2: Extension Ideas

**Task:** Choose one and tell Claude:

**Easy Extensions:**
- "I want to add a footer with my name and the data source"
- "I want to sort the table by date or time"
- "I want to add a title and favicon to the site"

**Intermediate Extensions:**
- "I want to add filtering to show only calls from certain neighborhoods"
- "I want to add charts showing calls by date or time of day"
- "I want to improve the detail page with more information"

**Advanced Extensions:**
- "I want to add a search feature"
- "I want to cluster nearby markers on the map"
- "I want to compare this week's data to other weeks"

**For each extension, Claude will:**
1. Ask clarifying questions about your goals
2. Explain the concepts involved
3. Implement the feature
4. Explain how it works
5. Help you test it

---

## Tips for Success

### Working with Claude Code

1. **Be specific**: Instead of "make it better," say "I want to add a header with navigation"
2. **Ask questions**: If you don't understand something, ask Claude to explain
3. **Iterate**: Start simple, then add features one at a time
4. **Review code**: Don't just accept code - make sure you understand it

### Debugging

When something goes wrong:

1. **Read error messages carefully** - they usually tell you exactly what's wrong
2. **Check your browser console** (F12) for JavaScript errors
3. **Use print statements** to see what data looks like
4. **Ask Claude**: "I'm getting this error: [paste error]. What does it mean and how do I fix it?"

### Git Best Practices

- **Commit often** with clear messages
- **Test before committing** - make sure it works
- **Push regularly** to back up your work
- **Use branches** for experiments

---

## Getting Help

### Ask Claude Questions Like:

- "Can you explain how [concept] works?"
- "Why did we do [X] instead of [Y]?"
- "I want to understand [part of code] better"
- "What would happen if I changed [X]?"
- "Can you show me another way to do [X]?"

### Debugging with Claude:

- "My page isn't loading - can you help me debug?"
- "The map isn't showing up - what's wrong?"
- "I'm getting this error: [error message]"
- "Why isn't my CSS applying?"

### Extending with Claude:

- "I want to add [feature] - how would I do that?"
- "Can you show me how to [task]?"
- "What's the best way to [goal]?"

---

## Next Steps

After completing this tutorial, you'll have:

- ✅ Built a complete news application
- ✅ Learned Flask, HTML, CSS, and JavaScript basics
- ✅ Worked with data and templates
- ✅ Created interactive maps
- ✅ Published a site to the internet

### Continue Learning:

1. **Explore the Flask documentation**: https://flask.palletsprojects.com/
2. **Learn more Leaflet**: https://leafletjs.com/examples.html
3. **Study other news apps**: Look at real news organization projects
4. **Build your own project**: Find a dataset you care about and visualize it!

### Other Data Sources:

- Police incident reports
- Restaurant inspections
- Campaign finance data
- Sports statistics
- Any public CSV dataset!

---

## Tutorial Structure Reference

For instructors or self-guided learners, here's the learning progression:

1. **Act 1**: Environment setup, git basics
2. **Act 2**: Flask framework, routing, templates
3. **Act 3**: Data loading, CSV parsing, displaying lists
4. **Act 4**: Dynamic routing, detail pages, 404 handling
5. **Act 5**: JavaScript integration, Leaflet maps, GeoJSON
6. **Act 6**: CSS styling, responsive design, custom assets
7. **Act 7**: Static site generation, GitHub Pages publishing
8. **Act 8**: Review, extensions, independent learning

Each act builds on previous knowledge while introducing new concepts.

---

## Ready to Start?

Begin with **Act 1** and tell Claude:

> "I'm ready to start the First News App tutorial. Let's begin with Act 1, Step 1.2. I want to personalize my README.md file."

Remember: This is an interactive learning experience. Don't just ask Claude to "do everything" - engage with each step, answer the understanding questions, and make sure you learn the concepts!

Happy coding! 🚀
