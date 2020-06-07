---
layout: post
title: Simple Editing Markup?
date: 2013-02-18 21:49
author: onionsamson
comments: true
categories: [Aza Raskin, CriticMarkup, Editing, github, gitosphrere, Tech, Writing]
---
<p><a href="http://criticmarkup.com/">CriticMarkup</a> is a new toolkit for editors to mark-up documents. It’s syntax appears to be quite simple. There are five types of Critic marks:</p>

<ul>
<li>Addition <em>{++ ++}</em>, e.g., <code>App{++les++}</code></li>
<li>Deletion <em>{-- --}</em>, e.g., <code>Orange{--s--}</code></li>
<li>Substitution <em>{~~ ~&gt; ~~}</em>, e.g., <code>{~~Tomato~&gt;Tomatoes~~}</code></li>
<li>Comment <em>{&gt;&gt; &lt;&lt;}</em>, e.g., <code>{&gt;&gt;Is a CriticMarkup’ed document going to be readable?&lt;&lt;}</code></li>
<li>Highlight &amp; Comment_ {== ==}_, e.g., <code>{==Will a CriticMarkup’ed document look like goobledygook?==}{&gt;&gt;Depends on what tool you’re going to view it with.&lt;&lt;}</code></li>
</ul>

<p>The <abbr title="Good guys and leeching tech-hipster culture writ large">Gitosphere</abbr> is already responding by integrating <em>CriticMarkup</em> into popular text-editors, such as <a href="http://multimarkdown.com/">MultiMarkdown Composer</a>.</p>

<p>In contrast to <em>CriticMarkup</em>, Aza Raskin’s <a href="http://www.azarask.in/blog/post/collaboration_made_simple_with_bracket_notation/">Bracket Notation</a> is an even more elegant and simple method, which makes a lot of sense and doesn’t require jazz-trumpet Vimeo tutorials to fully appreciate. The only deviation I make from Raskin’s method is, as suggested by <a href="http://koralatov.com">Koralatov</a>, to use curly brackets instead of square brackets which ensures it doesn't conflict with
Markdown's link syntax..</p>

<blockquote>
  <p>“The solution is simply three sets of square brackets and some customs: the first set of brackets denotes deletion, the second set denotes addition, and the third set denotes a comment. Apparently, a similar model is used to keep track of edits in the United Nations.”</p>
</blockquote>

<p>Examples of Bracket Notation:</p>

<ul>
<li>Delete <em>{}</em>, e.g., <code>I like green {oranges}.</code> <strong>becomes</strong> <code>I like green.</code></li>
<li>Add <em>{}{}</em>, e.g., <code>I like green {}{apples}.</code> <strong>becomes</strong> <code>I like green apples.</code> (because nothing is deleted and apples is added).</li>
<li>Substitute (Delete &amp; Add) <em>{}{}</em>, e.g., <code>I like green {oranges}{apples}.</code> <strong>becomes</strong> <code>I like green apples.</code> (because “oranges” is deleted and “apples” is added).</li>
<li>Editorial Comment <em>{}{}{}</em>, e.g., <code>Cats are evil. {}{}{Ed - You are a mean and likely unattractive cat-hater.}</code> (no changes are made but the editor has been offended by the author and left an unconstructive comment in response).</li>
<li>Substitution with Editorial Comment <em>{}{}{}</em>, e.g., <code>I like green {oranges}{steak}.{Paleo sense is tingling. Need more fresh meat.}</code> <strong>becomes</strong> <code>I like green steak.</code> (with an editors comment about paleo).</li>
</ul>

<p>Not to knock <em>CriticMarkup</em> too hard (I do think it’s neat and visually arresting), the beautiful, mathematic simplicity of bracket notation is hard to beat. As Raskin concludes:</p>

<blockquote>
  <p>“It’s a simple solution to a possibly complex problem. It shows that sometimes the solution to an interface problem doesn’t involve inventing something brand new, but reusing something old.”</p>
</blockquote>
