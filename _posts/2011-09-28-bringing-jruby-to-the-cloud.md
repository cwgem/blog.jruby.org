---
layout: post
title: Bringing JRuby to the Cloud
author: Charles Oliver Nutter
email: headius@headius.com
---

My friends, I'm proud to announce we've reached another milestone with JRuby: the full, non-beta, general availability of [Engine Yard Cloud's JRuby support](http://www.engineyard.com/blog/2011/jruby-ga-on-an-engine-yard-cloud-near-you/)!

The release of JRuby on our Cloud comes after years of work on JRuby and months of work by [David Calvera](http://twitter.com/calavera), [Hiro Asari](http://twitter.com/hiro_asari), and the awesome [stack team](http://docs.engineyard.com/appcloud-tech-stack.html) at Engine Yard. It is, in many ways, the "big goal" we had when [Tom Enebo](http://twitter.com/tom_enebo), [Nick Sieger](http://twitter.com/nicksieger) and [I](http://twitter.com/headius) came to Engine Yard in 2009 to continue working on JRuby. We're very excited to have accomplished our big goal for JRuby at Engine Yard, and will now look forward to new goals and milestones. But what does this mean to you? And how did we get here?

JRuby on Engine Yard Cloud
--------------------------

If you've ever used Engine Yard Cloud before, you already know what it feels like. JRuby support looks and feels pretty much the same; you just select JRuby from the Ruby versions drop-down, choose Trinidad, and deploy your app as normal. Provisioning, deployment, and migration all happen for you automatically. You can configure Trinidad to spin up enough JRuby instances to handle your concurrent load, or run "threadsafe" using a single instance. And that's it! You have your JRuby application in the cloud, with support from the best team in the Ruby cloud universe.

The Cloud's support for JRuby represents milestones for the wider Ruby world, too. It's obviously the first cloud to officially support JRuby, but it's also the first cloud with a concurrency-capable Ruby and the first cloud supporting an alternative Ruby implementation. You get the best cloud with the best support story and one of the best Ruby implementations on one of the best VMs in the world. What's not to love?

We at Engine Yard and on the JRuby team are very proud to have finally achieved this milestone. Let's take a look back at the past five years of JRuby that led us to this point.

A Brief History
---------------

I've talked about the history of JRuby in many posts, and I'm preparing one on JRuby's 10-year anniversary as you read this. The journey really started in 2006, when Tom and I first demonstrated JRuby running a Rails application at JavaOne. That was [JRuby 0.8.3](http://sourceforge.net/project/shownotes.php?release_id=405255), and six months prior we couldn't even run IRB. In those days, the JVM world was just starting to explore alternative languages, with most of that attention on Jython and Groovy. Scala, Clojure, and the other half-dozen "new" JVM languages you may have heard about were either still growing up or still hiding behind the curtain of academia.

That first demo saw JRuby running on WEBrick, because there were no other servers for JRuby yet. No native DB support existed for JRuby, so we had to get the pure-Ruby MySQL driver working. We were able to install gems and run IRB, but the Rails console didn't work and everything felt ready to fly apart. Just days before JavaOne, we got it working.

Tom and I were sitting at the Espresso Royale coffee shop near the University of Minnesota campus, walking through the basic CRUD operations and making sure everything functioned. It all seemed to work -- and that was very exciting -- but the performance was really dreadful. It took seconds for each page refresh, sometimes so long we thought the app had hung.

On a hunch, we started looking for Rails tuning advice. One page talked about something called "development mode" and highly recommended using "production mode" for production applications. Without any other leads, we flipped the switch...and the JRuby on Rails age dawned! Performance was not spectacular, but it was totally acceptable for a first public showing. Rails was running atop the JVM, and JRuby made it possible!

A year later, Tom and I had accepted positions at Sun Microsystems and were preparing to release [JRuby 1.0](http://blog.headius.com/2007/06/jruby-10-released.html) for JavaOne 2007. We were optimistic...we felt like JRuby was ready for simple, non-critical production apps, and we were eager to show the JVM world what we could do. This time, we had Nick Sieger's ActiveRecord-JDBC for database access and an early precursor to jruby-rack called "GoldSpike" (after the golden spike that joined east to west in the early USA rail system) to allow servlet engines to serve up Rails requests.

JRuby 1.0 was fully interpreted, quite slow, and far less Ruby-compatible than JRuby today, but it worked. And it was enough to draw in a few early production users like Oracle and Thoughtworks.

The next year saw the release of [JRuby 1.1](http://docs.codehaus.org/display/JRUBY/2008/04/05/JRuby+1.1+Released), the first Ruby implementation ever to incorporate a runtime just-in-time (JIT) compiler to improve performance. We were starting to beat Ruby 1.8 on simple benchmarks, and stability kept increasing.

JRuby has had many more releases, always focusing on the user's experience and the user's needs. JRuby 1.1.1 through 1.1.6 made huge leaps forward in compatibility and performance, and JRuby 1.2 may have been the first release *really* ready for production. [JRuby 1.3](http://www.jruby.org/2009/06/03/jruby-1-3-0.html), [1.4](http://jruby.org/2009/11/02/jruby-1-4-0), and [1.5](http://jruby.org/2010/05/12/jruby-1-5-0.html) each involved thousands of commits and hundreds of fixed bugs, along with more and more production users ranging from [airports](http://www.osl.no/en/osl) to the [Allen Telescope Array](http://www.seti.org/ata).

This year, we released [JRuby 1.6](http://jruby.org/2011/03/15/jruby-1-6-0.html) with Ruby 1.9 features and experimental support for C extensions, and have done four 1.6.x maintenance releases (with a fifth just around the corner). JRuby 1.7 will take advantage of the new "invokedynamic" support in Java 7, and runs far faster than any previous release.

JRuby is now more compatible and boasts better performance than ever before, and has earned a place in both the Ruby and Java worlds.

JRuby meets the Cloud
---------------------

The earliest talk about JRuby at Engine Yard started in late 2008. [Tom Mornini](http://twitter.com/tmornini) reached out to us, interested in talking about what a JRuby-powered Engine Yard offering might look like. We talked on and off with him and other Engine Yarders in early 2009, and finally visited the Engine Yard office to talk seriously about making something happen.

We were lost deep within another cloud: the cloud of doubt hanging over the Oracle takeover of Sun Microsystems. With change in the air, Tom, Nick and I accepted new positions at Engine Yard, and the wheels were set in motion for JRuby support.

It was a hard slog to get here. Engine Yard's cloud was under heavy development, marketing, and rebranding, so we kept cranking out JRuby releases and helping anyone with available cycles get to know JRuby better. In early 2010, Engine Yard hired Hiro Asari, a long time JRuby contributor also interested in making a move. Hiro became the first-ever-anywhere JRuby support engineer, and we launched official commercial support for JRuby later that year.

The arrival at engine yard of David Calavera, creator of the Trinidad server, finally gave us the missing piece needed for JRuby on Engine Yard Cloud. We went to alpha stage early in 2011 and to beta some months later for RailsConf.

With a few production users under our belt, we decided RubyConf 2011 was the right time to go to GA (general availability). And here we are!

Next Steps For You
------------------

Engine Yard wants to help you bootstrap your application, and to do so we're continuing to offer [500 free compute hours](http://engineyard.com/tryjruby). That applies to JRuby too, so there's really no reason *not* to give it a shot. If you've ever wanted to try deploying to JRuby, or if you've never played with Engine Yard Cloud, today is the day!

All the Engine Yard JRuby team members will also be at RubyConf this week, and we'll be holding continuous office hours wherever we stand (perhaps with some scheduled office hours too) to help you get started on Engine Yard Cloud, help you attempt a migration to JRuby, or just to hear what you want from JRuby. We've done all this work for you, the Rubyists and JRubyists of the world, and we want you to have the best experience possible!

Finally, I'd really like everyone to send a big "Thank You" to [@engineyard](http://twitter.com/engineyard) on Twitter. Without their support these past couple years, JRuby would not have made so much progress. Without a commercial support offering, several large JRuby users might never have used Ruby at all. And now, with official cloud support, deploying JRuby is a fire-and-forget proposition. Engine Yard helped us bring JRuby to maturity, and the Ruby world is a better place as a result.

Thank you all, friends, for your support these many years. I hope to hear from each and every one of you, and you can rest assured more great things are coming from JRuby and Engine Yard.