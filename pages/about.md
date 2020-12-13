---
layout: page
permalink: /about.html
title: 关于
tags: [关于, 博客, znfang, blog]
---

<div class="zh post-container">
    <!-- 增加了自动统计博客数量的功能，原理参照总字数的统计 -->
    <blockquote>
        知道越多，懂的越少
    </blockquote>
    <br>
    <h3>WHY BLOG</h3>
    <hr>
    <p>生命总是由不同的细节构成的，学会记录生活细节，丰满人生。
    本博客自2019年5月1日起开始运行至今，共
    {% assign papers = 0 %}
    {% for post in site.posts %}
    {% assign papers = papers | plus: 1 %}
    {% endfor %}
    {{ papers }}
    篇文章，总字数
    {% assign count = 0 %}
    {% for post in site.posts %}
    {% assign single_count = post.content | strip_html | strip_newlines | size %}
    {% assign count = count | plus: single_count %}
    {% endfor %}
    {% if count > 10000 %}
    {{ count | divided_by: 10000 }} 万 {{ count | modulo: 10000 }}
    {% else %}
    {{ count }}
    {% endif %}
    .</p>
    <br>
    <h3>ABOUT ME</h3>
    <p>本科毕业于上海大学，研究生毕业于浙江大学</p>
    <p>目前在一家银行做后端开发</p>
    <p>浪费了太多的时间在选择上，该静下心来做点事情了</p>
    <br>
    <h3>REWARD</h3>
        若您觉得鄙人所创造的内容对您有所帮助，可考虑略表心意，支持本博。
        以下是微信赞赏码：
    <div style="text-align: center;">
       <img src="/img/wechat-reward.png" style="width:30%;margin:0 auto;" />
    </div>
    <br>
    <h3>THANKS</h3>
    <hr>
    <p>本博客的主题来自<a href="https://blog.fooleap.org/" target="_blank">fooleap</a>，很喜欢这种简单明快的风格。感谢Jekyll、GitHub Pages。</p>

</div>


