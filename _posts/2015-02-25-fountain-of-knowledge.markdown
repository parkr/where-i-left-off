---
layout: post
title: "Fountain of Knowledge"
date: "Wed Feb 25 08:01:16 -0800 2015"
---

- [Why James Baldwin's FBI File was 1,884 Pages Long](http://publishersweekly.com/pw/by-topic/industry-news/tip-sheet/article/65641-why-james-baldwin-s-fbi-file-was-1-884-pages.html)
- [A GUIDE TO THE MEANING AND USEFULNESS OF PUNCTUATION MARKS.](http://www.mcsweeneys.net/articles/a-guide-to-the-meaning-and-usefulness-of-punctuation-marks)
- [What ISIS Really Wants](http://www.theatlantic.com/features/archive/2015/02/what-isis-really-wants/384980/)
- [The billionaire's typewriter](http://practicaltypography.com/billionaires-typewriter.html)
- ["Promoting Economic Competitiveness while Safeguarding Privacy, Civil Rights, and Civil Liberties in Domestic Use of Unmanned Aircraft Systems"](https://docs.google.com/file/d/0BwNqWeg2Hs1JSWJrZ0dpZWhjVzA/view?sle=true) <-- drones
- [Handling five billion sessions a day – in real time](https://blog.twitter.com/2015/handling-five-billion-sessions-a-day-in-real-time)
- [List of all SFHTML5 presentations and videos](bit.ly/sfhtml5videos)
- [C9 Lectures: Dr. Graham Hutton - Functional Programming Fundamentals Chapter 11 of 13](https://www.youtube.com/watch?v=rlwSBNI9bXE)
- [Introducing “6-pack”: the first open hardware modular switch](https://code.facebook.com/posts/717010588413497/introducing-6-pack-the-first-open-hardware-modular-switch/)
- [Godoc: Documenting Go Code](http://blog.golang.org/godoc-documenting-go-code)
- [High-Performance Go](http://talks.golang.org/2013/highperf.slide#26)

In particular, the select statement here:

{% highlight go %}
func myHandler(w http.ResponseWriter, r *http.Request) {
    c := appengine.NewContext(r)
    // ...
    // regular request handling
    // ...

    // Save to memcache, but only wait up to 3ms.
    done := make(chan bool, 1) // NB: buffered
    go func() {
        memcache.Set(c, &memcache.Item{
            Key:   key,
            Value: data,
        })
        done <- true
    }()
    select {
    case <-done:
    case <-time.After(3 * time.Millisecond):
    }
}
{% endhighlight %}
