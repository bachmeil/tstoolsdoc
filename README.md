# tstoolsdoc

I'm very slowly adding documentation of the tstools package functionality. It's unlikely I'll ever create a "correct" R package with a full manual. Life's too short to spend it on that.

If you want to build it yourself, you need Pandoc and a recent version of Perl installed. The process to add another documentation page is simple:

- Write out the page in the md/ directory.
- Add an entry somewhere in the md/index.md file.
- Run the build script to add that file. For instance, if you write newfunction.md, then run `h newfunction` and you'll end up with newfunction.html in the docs/directory and you'll have an updated index file.

Once you do that, you can open index.html in the browser and start navigating.

Pull requests welcome. Since I'm not able to review, edit, and merge documentation written by others in a timely fashion, you should feel free to post documentation and examples [on the wiki](https://github.com/bachmeil/tstoolsdoc/wiki) (which is open to the public for editing). That's a public space. You don't need anyone's permission to post something there as long as it's related to tstools and it's not intentionally inaccurate. I may add official pages linking to your wiki entry.

There's a [discussion board](https://github.com/bachmeil/tstoolsdoc/discussions) for any questions. Given the number of users of the tstools package, there will hopefully be someone to answer your question.
