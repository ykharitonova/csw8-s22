# Just the Class

Just the Class is a GitHub Pages template developed for the purpose of quickly deploying course websites. In addition to serving plain web pages and files, it provides a boilerplate for:

- a [course calendar](calendar.md),
- a [staff](staff.md) page,
- and a weekly [schedule](schedule.md).

Just the Class is a set of customizations on top of the popular [Just the Docs](https://github.com/pmarsceill/just-the-docs) theme, which provides a robust and thoroughly-tested foundation that makes it easy to extend for your own special use cases. These foundational features include:

- automatic [navigation structure](https://pmarsceill.github.io/just-the-docs/docs/navigation-structure/),
- instant, full-text [search](https://pmarsceill.github.io/just-the-docs/docs/search/) and page indexing,
- and a small but powerful set of [UI components](https://pmarsceill.github.io/just-the-docs/docs/ui-components) and authoring [utilities](https://pmarsceill.github.io/just-the-docs/docs/utilities).

## Getting Started

Getting started with Just the Class is simple.

1. Create a [new repository based on Just the Class](https://github.com/kevinlin1/just-the-class/generate).
    - for CSW8, use the previous course repo to minimize the setup time: 
    - W22 ([github](https://github.com/ucsb-csw8/w22) / [web](https://ucsb-csw8.github.io/w22/)) → S22 ([github](https://github.com/ucsb-csw8/s22) / [web](https://ucsb-csw8.github.io/s22/))
1. Update `_config.yml` and `index.md` with your course information.
1. Configure a [publishing source for GitHub Pages](https://help.github.com/en/articles/configuring-a-publishing-source-for-github-pages). Your course website is now live!
1. Edit and create `.md` [Markdown files](https://guides.github.com/features/mastering-markdown/) to add your content.
    - `_config.yml`- update first - its contents are not auto-refreshed like the .md pages do. To see the changes to its contents, stop/restart Jekyll
    - `about.md` - make sure to update the Syllabus and course policies
    - `announcements.md` - skip, if not using the website Announcements
    - `calendar.md` - the information from this file is displayed at the top of the page that lists weekly topics and due dates;
        - if not using reflections, make sure to comment-out that part of the instructions. 
        - The Calendar is populated using the files in the `_modules` folder. These are added semi-automatically, using a script `generate_due_dates.py` that hard-codes start and end dates, etc.
    - `faq.md` - make sure to update the QnA based on your course information. After you update the Syllabus and the Calendar, make sure you address the typical first-week questions and clarify the `#weekly-pattern-and-planning-your-work` section
    - `index.md` - the front page of the course; some of the info there, like the course title, come from the `_config.yml` file 
    - `jekyll.sh` - no need to change: run it as a shortcut to running the `bundle` command
    - `quiz.md` - make sure to update the instructions based on your course quiz structure and policies
    - `schedule.md` - the information for it is pulled from the `_schedules/weekly.md` --> make sure to update the latter - usually done via a script
    - `staff.md` - the information for it is pulled from the `_staffers` and images are in the `assets/images` --> make sure to update them (see the `_example.md` to help you get started with a template) 
    - `success.md` - make sure to change the **Roadmap** to align with your course calendar

* For the `ref/` folder, I recommend initially comitting the `goals.md`, since it's referenced in the Syllabus and `keyboard.md`; the rest of them can be added later, when they become relevant.
* Initial commit included the following files: `README.md _announcements _config.yml _includes/ _layouts/ _modules/ _sass/ about.md announcements.md assets/ calendar.md faq.md index.md jekyll.sh ref/goals.md ref/keyboard.md schedule.md staff.md success.md`


Just the Class has been used by instructors at Stanford University ([CS 161](https://stanford-cs161.github.io/winter2021/)), UC Berkeley ([Data 100](https://ds100.org/fa21/)), UC Santa Barbara ([DS1](https://ucsb-ds.github.io/ds1-f20/)), Northeastern University ([CS4530/5500](https://neu-se.github.io/CS4530-CS5500-Spring-2021/)), and Carnegie Mellon University ([17-450/17-950](https://cmu-crafting-software.github.io/)). For a few open-source examples, see the following course websites and their source code.

- [CSE 390HA](https://courses.cs.washington.edu/courses/cse390ha/20au/) ([source code](https://gitlab.cs.washington.edu/cse390ha/20au/website)) is an example of a single-page website that centers modules.
- [CSE 143](https://courses.cs.washington.edu/courses/cse143/20au/) ([source code](https://gitlab.cs.washington.edu/cse143/20au/website)) hosts an entire online textbook with full-text search.
- [CSE 373](https://courses.cs.washington.edu/courses/cse373/21su/) ([source code](https://gitlab.cs.washington.edu/cse373-root/21su/website)) is an example of a simple website combining Markdown pages with generated HTML files.

Share your course website and find more examples in the [show and tell discussion](https://github.com/kevinlin1/just-the-class/discussions/categories/show-and-tell)!

Continue reading to learn how to setup a development environment on your local computer. This allows you to make incremental changes without directly modifying the live website.

### Local development environment

Just the Class is built for [Jekyll](https://jekyllrb.com), a static site generator. View the [quick start guide](https://jekyllrb.com/docs/) for more information. Just the Docs requires no special Jekyll plugins and can run on GitHub Pages' standard Jekyll compiler.

1. Follow the GitHub documentation for [Setting up your GitHub Pages site locally with Jekyll](https://help.github.com/en/articles/setting-up-your-github-pages-site-locally-with-jekyll).
1. Start your local Jekyll server.
```bash
$ bundle exec jekyll serve
```
1. Point your web browser to [http://localhost:4000](http://localhost:4000)
1. Reload your web browser after making a change to preview its effect.

For more information, refer to [Just the Docs](https://pmarsceill.github.io/just-the-docs/).
