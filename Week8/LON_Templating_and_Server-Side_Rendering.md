# Templating and Server-side rendering

* What is server-side rendering?
* What are the pros and cons of serverside rendering vs clientside
* What problems do templating languages solve
* What are some examples of functionality that templating languages provide e.g. conditional logic etc.

## What is Server-Side Rendering?
Display web page on client computer by server sending all the html contents

Affecting factors:

* your internet speed
* the location of the server
* how many users are trying to access the site
* and how optimized the website is, to name a few

#### Diagram of server-side rendering
![](https://i.imgur.com/H9OHlQB.png)

## Server-Side Rendering vs. Client-Side Rendering

#### Diagram of Client-Side rendering
![](https://i.imgur.com/neQXnvH.png)
-

| Server-side pros | Server-side cons |
| -------- | -------- |
| Search engines can crawl the site for better SEO | Frequent server requests |
|The initial page load is faster | An overall slow page rendering |
| Great for static sites| Full page reloads |
|  | Non-rich site interactions |


| Client-side pros | Client-side cons |
| -------- | -------- |
| Rich site interactions | Low SEO if not implemented correctly |
| Fast website rendering after the initial load | Initial load might require more time |
| Great for web applications |  |

![](https://media.giphy.com/media/l3nWs80J0RNSCfZh6/giphy.gif)

#### Best of Both Worlds - (*Isomorphic web frameworks*)
You can get the best of both worlds by using server-side rendering for the initaial load of the site and then switching to client-side rendering for any updates.

* For the first page load, it doesn’t take two round trips to the server before the user sees content.
* Subsequent page loads are lightening fast.
* Crawlers get their simple HTML. Just like the old days. No need to do the work of running JavaScript. Or dealing with _escaped_fragment_.For the first page load, it doesn’t take two round trips to the server before the user sees content.

**BUT** this does add to the complexity of the site and is generally not neccessary.


## What problems do templating languages solve
A templating language allows defining placeholders that should later on be replaced for the purpose of implementing designs. 

Templating engines allow the data to change without duplicating the code.

Which makes it:
* maintainable
* easy to update
* saves on excessive DOM manipulation

## Handlebar Examples

![](https://media.giphy.com/media/11UzbTpybT6Ypy/giphy.gif)

![](https://i.imgur.com/4B3LrU0.png)

What is a handlebar?

![](https://i.imgur.com/fke76xY.png)

![](https://i.imgur.com/RhRafcU.png)

![](https://i.imgur.com/f0V9WBO.png)

![](https://i.imgur.com/mb7jp3Z.png)

![](https://i.imgur.com/Jv52Rll.png)

![](https://i.imgur.com/qS2C01p.png)

### Variables

*Handlebars:*
```
<h1>{{name}}</h1>
<p>{{location}}</p>
```

*Data:*
```
{
  name: "Sangita",
  location: "London"
}
```

*Renders:*
```
<h1>Sangita</h1>
<p>London</p>
```

### Iteration

*Handlebars:*
```
<div>
  {{#each languages}}
    <p>{{@index}}. {{this}}</p>
  {{/each}}
</div>
```

*Data:*
```
{
  languages: ['html', 'css', 'javascript']
}
```

*Renders:*
```
<div>
  <p>0. html</p>
  <p>1. css</p>
  <p>2. javascript</p>
</div>
```

### Conditions (**if**)

*Handlebars:*
```
{{#if user.admin}}
  <button class="launch">Launch Spacecraft</button>
{{else}}
  <button class="login"> Log in</button>
{{/if}}
```

*Data:*
```
{
  user: {
    admin: true
  }
}
```

*Renders:*
```
<button class="launch">Launch Spacecraft</button>
```

### Conditions (**unless**)

*Handlebars:*
```
{{#unless user.admin}}
  <button class="login"> Log in</button>
{{else}}
  <button class="launch">Launch Spacecraft</button>
{{/unless}}
```

*Data:*
```
{
  user: {
    admin: true
  }
}
```

*Renders:*
```
<button class="launch">Launch Spacecraft</button>
```

### Block Expressions

*Handlebars:*
```
{{#with user}}
  <p>{{name}}</p>
    {{#with contact}}
      <span>Twitter: @{{twitter}}</span>
    {{/with}}
  <span>Address: {{address.city}},
{{/with}}
{{user.address.country}}</span>
```

*Data:*
```
{
  user: {
    contact: {
      email: 'sangita@gmail.coms',
      twitter: '@sunuwars'
    },
    address: {
      city: 'London',
      country: 'England'
    },
    name: 'Sangita'
  }
}
```

*Renders:*
```
<p>Sangita</p>
<span>Twitter: @sunuwars</span>
<span>Address: London, England</span>
```

### Comments

Either

`{{! handlebar comment }}`

or

`
{{!-- handlebar comment --}}
`

### Double or Triple Braces?

If you don't want Handlebars to escape a value, use triple curly braces: `{{{ unescaped output }}}`.

*Handlebars:*
```
<ul>
   {{#each arr}}
    <li>
      <span>{{@index}}</span>
      <span>unescaped: {{{this}}} vs. </span>
      <span>escaped: {{this}}</span>
    </li>
  {{/each}}
</ul>
```

*Data:*
```
{
  arr: [
    '<a>a</a>',
    '<i>italic</i>',
  ]
}
```

*Renders:*
```
<ul>
  <li>
    <span>0</span>
    <span>unescaped: <a>a</a> vs. </span>
    <span>escaped: &lt;a&gt;a&lt;/a&gt;</span>
  </li>
  <li>
    <span>1</span>
    <span>unescaped: <i>italic</i> vs. </span>
    <span>escaped: &lt;i&gt;italic&lt;/i&gt;</span>
  </li>
</ul>
```

![](https://media.giphy.com/media/ehA575gOh0RIQ/giphy.gif)
