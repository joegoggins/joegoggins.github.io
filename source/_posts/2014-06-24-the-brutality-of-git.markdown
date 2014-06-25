---
layout: post
title: "The brutality of Git"
date: 2014-06-24 22:53:58 -0500
comments: true
categories: 
---

I love Git. Live by it. Swear by it. Interact with it all the damn time. I mostly love it.

Sometimes it stabs me in the face though...while on master:

    # Grab the latest
    git pull

    # Deploy a branch to heroku: 
    git push --force staging feature/the_awesome_sauce:master

Then boom, the shank to the face:

**feature/the_awesome_sauce is not deployed like I think**

Instead, a old commit from the feature/the_awesome_sauce is deployed, arrrrr...

They be different:

    the_project$ git show-ref feature/the_awesome_sauce
    6c9900faca9g2d758bf6g00a7418af37b315f3a7 refs/heads/feature/private_libraries
    ecc4c76220c5d399c0e1d53e950e456a4329ad56 refs/remotes/origin/feature/private_libraries

Don't get stabbed in the face. Know the difference between remote and local branches.

Use `git push --force staging origin/feature/the_awesome_sauce:master` next time.
