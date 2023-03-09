---
layout: default
title: Overview
nav_order: 0
---

{: .warning }
> THIS GUIDE IS STILL A DRAFT

<button class="btn js-toggle-dark-mode">Dark mode</button>

# App Engine Management Center
{: .fs-9 }

In this lab, you will get hands-on experience setting up and managing AEMC.
{: .fs-6 .fw-300 }

We will cover concepts such as Pipelines and Deployments, Onboarding Developers, and Collaborations.
{: .fs-6 .fw-300 }

{: .highlight }
> The content in this guide applies to App Engine Studio Version 22.0.3

[Lab 0][Lab0]{: .btn .btn-purple} | Start here to get an overview of App Engine.
[Lab 1][Lab1]{: .btn .btn-purple } | Configure the basics of AES, including the Pipeline. 
[Lab 2][Lab2]{: .btn .btn-purple } | Manage who can use AES and collaborate on apps. 
[Lab 3][Lab3]{: .btn .btn-purple } | Set up the system to allow people to apply to build apps. 
[Lab 4][Lab4]{: .btn .btn-purple } | Approve apps for deployment and move them through the pipeline. 
[Lab 5][Lab5]{: .btn .btn-purple } | Application Templates




[Lab0]: /lab_0_prepare/
[Lab1]: /lab_1_configure
[Lab2]: /lab_2_manage
[Lab3]: /lab_3_manage
[Lab4]: /lab_4_Manage_App_Deployment/
[Lab5]: /lab_5_Bonus_Info/

<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XJ4NRHHVXR"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-XJ4NRHHVXR');
</script>

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode');

jtd.addEvent(toggleDarkMode, 'click', function(){
  if (jtd.getTheme() === 'dark') {
    jtd.setTheme('light');
    toggleDarkMode.textContent = 'Dark mode';
  } else {
    jtd.setTheme('dark');
    toggleDarkMode.textContent = 'Light mode';
  }
});
</script>