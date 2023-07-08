## Interactive Code Playgrounds (ICPs)
#### A slides system to make university programming classes more active and inclusive

This project is part of my dissertation for my Master's degree in Computer Science.

The dissertation explores the potential of Interactive Code Playgrounds (ICPs) as a tool for enhancing University programming education, particularly introductory courses. It promotes an engaging, inclusive and active learning environment, consisting of slides with execution capabilities and exercises. Through a series of interventions conducted in introductory programming courses, the effectiveness and limitations of this tool were evaluated. The findings revealed that while certain programming languages and browser compatibility issues exist, students appreciated the interactivity and user-friendliness of ICPs, and found the resulting pedagogy more productive. The research lays the groundwork for future advancements in University programming education through the refinement of ICPs.

The ICPs project is composed of several modules, each designed to provide a specific feature. The most important ones are `icp-bundle`, `icp-create-server` and `icp-editor`.

`icp-bundle` is a plugin that offers code playgrounds exposed as web components. It supports various programming languages, including Javascript/Typescript, Python, Java, Processing, StandardML, C/C++ and SQL. The module was developed using the Svelte framework, and it leverages the power of WebWorkers or SharedWorkers to handle resource-intensive tasks such as code compilation and execution. The communication pattern used to pass messages between components in a child-parent relation is based on CustomEvents, capable of propagating across Shadow DOM boundaries. The code editor is built on CodeMirror 6, and it has been customized with plugins to fulfill our requirements. The build process relies on Vite, Gulp and a set of configuration files that allow to maintain modular outputs. The resulting files can be imported and used within web pages, allowing the creation of interactive code playgrounds using custom HTML tags such as `<python-editor />`.

The `icp-create-server` project automates the creation of single-file distributable web servers, which are essential for providing students with didactic material that can be used offline. The base file we start with is an executable ZIP archive that contains all the resources that will be served on localhost when executed, and this project simply inserts into this archive an index.html file containing the slides. To achieve this functionality in Javascript, we developed a script that operates at byte-level and adheres to the ZIP standard. The resulting NPM package exposes a function that takes a hexadecimal representation of the original ZIP file and the HTML content of the slides as input, and returns a Uint8Array with the updated ZIP archive.

The `icp-editor` module is a user-friendly ”What You See is What You Get” (WYSIWYG) editor that enables the creation of slides compatible with ICPs. It uses Reveal.js as the underlying presentation framework, and it provides a visual interface for designing the slides. The module is built with Svelte, and it uses Vite for efficient development and bundling. The editor is publicly served on Github Pages, allowing users to easily access it.

For the Java integration, I used a customized version of TeaVM and TeaVM-Javac, available as a fork on my GitHub profile.