[Tobacco Bootstrap](http://noroutine.github.com/tobacco-bootstrap)
==================

HTML5 Java web app archetype with latest and gratest components.

I always thought Java can do no less than RoR or any other fancy whistle framework out there without any mimicking aka Roo. So I decided to create this client-centric archetype that is always packed with latest JS and Java libraries, uses all the latests best practices and called it Tobacco because it's addictive!

Tobacco's focus is on providing modern stuff inside and make it easy to start a project with best of breed HTML5 templates and JavaScript libs, so you don't spend hours settings up the project, downloading libraries and placing them in correct locations. With Tobacco you always get's this done for you. All you need is generate your project and start coding.

Tobacco shows how Java can do modern projects in 5 seconds in it's own style. It doesn't dictate you to three-tiers if you do something simple, nor does it tells you which persistence layer to use, instead it tries its best to save your time on starting and setting up new web project and not be in the way after that.

Demo
----

Real website is worth thousands of words, so I setup [Tobacco Demo](http://zion.noroutine.me:8080/tobacco-demo) for you to check.

What's inside
-------------

All components are of latest versions. I'll continue to update this archetype with latest versions.

Client-side stuff 
* [Twitter Bootstrap 2.3.0](http://twitter.github.com/bootstrap/) for your UI to not suck
* [HTML5 boilderplate 4.1.0](http://html5boilerplate.com/) for your result HTML to use best practices available
* [Modernizr.js 2.6.2](http://modernizr.com/) to make your app display good on anything
* [Normalize.css 1.1.0](http://necolas.github.com/normalize.css/) for your app to look consistent
* [jQuery 1.9,1](http://jquery.com/) for you to write less and do more
* [Backbone.js 0.9.10](http://backbonejs.org/) to make your JS code to be organized more MVC-ish
* [LoDash.js 1.0.1](http://lodash.com/) to give you powerful common library
* [dust.js 1.2.0](http://linkedin.github.com/dustjs/) for you to use the fastest client-side templating engine on the planet
* [dust4j 0.2](http://dust4j.noroutine.me/) to let you write your templates in pure JSP and make them dynamic

Server-side stuff
* [Spring 3.2.1](http://www.springsource.org/) for wiring your components
* [Spring Security 3.2.0M1](http://www.springsource.org/) for your app to be secure
* [Tiles 3.0.1](http://tiles.apache.org/) to organize your views

There is some dozen of other smaller and less important stuff that you find adding to any new project all the time, because it's useful or just convenient. 

* serialize model objects to JSON right in your JSP with special tag, allows to easily bootstrap Backbone models
* automatic compression and aggregation of JS and CSS
* [common.js](https://github.com/noroutine/tobacco-demo/blob/master/tobacco-demo-webapp/src/main/webapp/js/common.js) adds UUID and Base64 support among other things
* [ResourceController](https://github.com/noroutine/tobacco-demo/blob/master/tobacco-demo-webapp/src/main/java/me/noroutine/ResourcesController.java) automatically exposes your i18n resources to JS so you can reuse them
* [@IfNoneMatch](https://github.com/noroutine/tobacco-demo/blob/master/tobacco-demo-webapp/src/main/java/me/noroutine/cache/IfNoneMatch.java) annotation lets you make your responses cacheable by browser

How to use
----------
_Make sure you have the latest Maven installed, at least version 3.0.4 is required_

Starting from 1.0.8, the generation of Tobacco projects is super-simple one-liner.
Anytime you are ready to rock the world with new project:

    mvn me.noroutine:tobacco:generate

This will automatically use the latest Tobacco Bootstrap version found in Maven Central.

Now your project is generated, it is required to setup SCM. git is meant to be used (.gitignore is already there for you).
    
    cd <app-name>
    git init
    git add -A
    git commit -a -m 'initial commit'

Now you're ready to go:

    cd <app-name>-webapps
    mvn package t7:run

after few minutes of terrifying console output, you can hope to access your new app at `http://localhost:8080/<app-name>`

### Can that be made even shorter?

Yes. With some extra configuration, you can save yourself from typing plugin groupId (me.noroutine). To do this, you
need to add me.noroutine to pluginGroups list in your `settings.xml` file:

    <!-- Somewhere in ~/.m2/settings.xml -->
    <pluginGroups>
        <pluginGroup>me.noroutine</pluginGroup>
    </pluginGroups>

After this you will be able to generate projects with a no-brainer:

    mvn tobacco:generate

After that, you still need to setup git.

### Is it really obligatory to use Git?

No. You can use SVN, or even go ahead without SCM. In SVN case, you will need to setup <scm /> section in pom.xml.
In case you decide to go ahead without SCM, the project will still run, but browser resource caching may not work
quite as expected. This is because source code revision is used for checking ETag. so make sure to clean your cache
if your code is not being executed.

The reason to use Git is it can be setup without central repository or internet.

### What if I don't need TB?

Work of H5BP and TB was combined and Bootstrap is used by default, but
you can still easily fallback and use plain H5BP if you don't intend to use TB

### About JPA, database access and security

I didn't bother to configure JPA to create another zillion-and-one archetype for 3-tier Spring web app.
It's not cool and overkill to require full-blown JPA persistence and/or ORM mapping for any project.
If you need it - you can still set it up though.

All needed stuff is still there for you to configure or remove at all if you don't need it - it's just commented out and not used from start.

As for security, there is simple form authentication workflow setup with single user, just to give you something to start with.
That way you can use home page for experiments and for more serious work you have boring stuff done for you already.

Profiles
--------

Project generated from Tobacco Bootstrap has three profiles:
* development(default) - development version of JS and CSS are used, moderate logging
* production - minified versions of JS and CSS are used, only errors are logged
* debug - same as development, but maximum logging

Switch between them from your IDE, or in command-line add `-P<profile>` as option to `mvn`

Thanks
------

Thanks to [H5BP](http://html5boilerplate.com/) and [TB](http://twitter.github.com/bootstrap/) guys. You're the best and I just love you!

Thanks to [GitHub](https://github.com/) and [Sonatype](https://oss.sonatype.org/index.html), your service is awesome.

Thanks to Maven guys, you made this possible (http://maven.apache.org/).
