---
layout: post
author: Abhi
title:  "My unique CKAD experience"
categories: certifications kubernetes
background: /assets/images/helm.jpg
img_credits:
  name: Joseph Barrientos
  url: https://unsplash.com/@jbcreate
  website: Unsplash
---
So, I passed the CKAD exam and I thought I'd share my unique experience.

> TL;DR: Practice, practice and practice. Improve your YAML and VIM skills. Good luck!

![practice](https://media.giphy.com/media/B1uajA01vvL91Urtsp/giphy.gif){:class="img-fluid"}

Just to be clear, there are 2 kinds of kubernetes certifications and I took the `developer` one.
<br>
If you are planning on it, you might want to read the description below to see which of these are you more interested in.
I have seen folks taking both the exams :man_shrugging:

> The Certified Kubernetes Administrator (CKA) certification  is designed to ensure that certification 
> holders have the skills, knowledge, and competency to perform the responsibilities of Kubernetes Administrators

> The Certified Kubernetes Application Developer (CKAD) certification is designed to provide assurance that CKADs have 
> the skills, knowledge, and competency to perform the responsibilities of Kubernetes application developers

More info [here](https://www.cncf.io/certification/cka/faq/)

## Not so long ago

It all started when I purchased the Linux Foundation's thanksgiving deal (course + exam under $200) with no **retakes**.

The Linux foundation course was good but I soon lost interest like most of us do and stopped preparing for a while.

Fast forward to April 2020, just then I had passed my Elasticsearch certification(which I'll write about it soon) and was motivated to take up another certification since we were all sheltering in place during the pandemic.

## Courses that helped me

### Pluralsight

Pluralsight came up with a free learning for the month of April and I started looking at CKAD courses. I had taken Nigel Poulton's courses on docker before and they were the best (still is).

The courses that helped me the most were 
- [Getting started with Kubernetes](https://app.pluralsight.com/library/courses/getting-started-kubernetes) by `Nigel Poulton`
- [CKA courses](https://app.pluralsight.com/paths/certificate/certified-kubernetes-administrator) by `Anthony Nocentino`.

If you are new to kubernetes, I definitely recommend going through both the courses to get your basics right.

### KodeKloud

KodeKloud's [CKAD course](https://kodekloud.com/p/kubernetes-certification-course) by `Mumshad Mannambeth` solidified what I had learnt so far. The best part of this course is that it has practice tests for each topic which will help you learn by doing it.

### Github

After these 2 courses, it was time to practice. There are handful of CKAD exercises on github but I did this one from [dgkanatsios](https://github.com/dgkanatsios/CKAD-exercises)
I already had a cluster setup in Linux Academy which proved handy for practising.

> Soon I realized that learning and understanding of the concepts were not enough, it's vital that you develop speed and agility in understanding and solving the problems.

## Text Editor

Know your text editor well since the exam is entirely in command line and you can choose your editor available in Linux environment `Nano` or `Vim` and I chose `Vim`.

And, I'm one of those who never liked `Vim` before :roll_eyes: and that was about to change.
I spent good few days to practice Vim and learn all the necessary shortcuts.

Here's my `.vimrc` config that I used for the exam

```vim
syntax on

set nu ic is ai et st=2 sw=2 pt=<F2>
```

- `syntax on` - good for syntax highlighting
- `nu` - shows line numbers
- `ic` - ignore case while searching
- `is` - incremental search
- `ai` - auto indent
- `et` - expand tabs to spaces
- `st=2` - indent using 2 spaces when you use tab
- `sw=2` - shift width 2 spaces
- `pt=<F2>` - paste toggle when you press F2 key

All these options are helpful when writing yaml definition files, copying yaml configurations from docs, searching, etc

I took few `.vimrc` options from [here](https://blog.codonomics.com/2019/09/essential-vim-for-ckad-or-cka-exam.html)

## Imperative commands

There are 2 ways to create resources in Kubernetes.
- The **declarative** way with yaml and applying the configuration with `kubectl apply`
    - For example you have the following yaml config to create a pod names `nginx.yaml`
      
      ```yaml
      apiVersion: v1
      kind: Pod
      metadata:
        name: nginx
      spec:
        containers:
        - name: nginx
          image: nginx
      ```
        
        To create the nginx pod you run the command <br> `kubectl apply -f nginx.yaml`
        
- **Imperative** way will create the resources without explicitly creating the yaml file.
    - The same nginx pod can be created using <br> `kubectl run nginx --image=nginx`

Get good with creating resources the imperative way. This will save you a lot of time during the exam.

## kubectl aliases

Create kubectl aliases so that you don't have to type the entire command.
> Remember you'll have 120 minutes to answer 19 questions, ~**6.3 minutes/question**.

My aliases. And make sure you add them to the `.bashrc` file as well

```
alias k=kubectl
alias kaf='k apply -f'
export do=‘—dry-run=client -o yaml’
alias kdr='k create $do’ # kubectl create resource with dry run
alias kdrp='k run $do’ # kubectl run pod with dry run
alias kn='k config set-context --curent --namespace' # set namespace
alias c=clear
```

So, if you had to create a deployment with dry run option you would just do `kdr nginx --image=nginx`

## Tips

- Understand the basics of kubernetes and the different ways to create and edit a resource. There would be questions around editing an existing deployment/pod.
- You will have access to kubernetes documentation and get good at searching the documentation
- Familiarity around listing resources for debugging purposes
    - `kubectl get <resource> -o wide` for listing additional details on the resource in the current namespace
    - `kubectl get <resource> --all-namespaces` for listing resources across all namespaces
    - `kubectl get <resource> -o yaml` gets the resource's yaml
- Describe and Explain commands are your best friends `kubectl describe pods my-pod` `kubectl explain pods`
- For a quick glance kubernetes [cheatsheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/) is quite helpful
- Always save a copy of the resource's yaml before deleting it
- Know your text editor well and definitely configure shortcuts for quick access
- Get familiar with basic linux commands like creating a file, appending to an existing file, etc
- Get good with creating resources the imperative way
- Try to attempt all the questions. Don’t spend too much time on one question
- Skip the questions with weight < 3% if it takes a long time

## My exam experience

Congratulations! You almost made it.

Now that I had prepared for several months, I felt I was ready for the exam. So, I booked a date.

Come exam day, fed my dog, logged in early and waited for the proctor to finish the formalities.

Once I got the green signal, the proctor released the exam.
Usually you'd see the questions on the left hand side and the in-browser command line on the right hand side where all the magic should happen.
Unfortunately, once I started typing on the command line, it went blank and I couldn't see what I typed or the result of the command.

I thought something's wrong with the exam environment and explained this to the proctor and they gave me a new exam environment.
And again the same experience and now I can see myself panicking a bit when I saw the time remaining :scream:

![this_is_not_fine](https://media.giphy.com/media/1FMaabePDEfgk/giphy.gif){:class="img-fluid"}

I was using an older version of MacBook Pro (2011) High Sierra (Don't you judge me!)
Luckily I had a chromebook and I asked the proctor if I could switch laptop real quick and they agreed! :smile:

Logged in real quick on my chromebook and after completing the formality, off I went.
I wasn't able to attend all the questions but I was confident on the ones I did.

Finally, the result came after couple of days and I had passed the exam!

![celebrate](https://media.giphy.com/media/Is1O1TWV0LEJi/giphy.gif){:class="img-fluid"}

I would encourage you to try and use the latest mac/laptops or one that isn't old as mine!

#### I wish you Good luck on your exam!

![you_got_this](https://media.giphy.com/media/1xVbRS6j52YSzp9P7N/giphy.gif){:class="img-fluid"}

Leave a comment on your experience.

#### Keep calm and kubectl :v:
