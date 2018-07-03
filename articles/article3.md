[< Back](../README.md)

# The BEM way

CSS is easy I would say, mainly because you can see quickly what we're doing. However, of course there are some negative points, one of them is related to the maintenance of it.

Open a file and writing CSS is very easy and quick, however, give maintenance, organize it and scale it are not. As your project grows, the trend of you start to lose patience with CSS gets bigger and bigger.

## BEM

There are several solutions that attempt to correct and assist in this matter of how to organize and structure the CSS of a project. One is the BEM (Block Element Modifier), which was created by the Yandex guys, a Russian search site.

According to BEM's website: "BEM is a highly useful, powerful, and simple naming convention that makes your front-end code easier to read and understand, easier to work with, easier to scale, more robust and explicit, and a lot more strict".

"This ensures that everyone who participates in the development of a website works with a single codebase and speaks the same language. Using proper naming will prepare you for the changes in design of the website".

## Example

The basic idea is to have three things:

- Block - like a component, the parrent.
- Element - parts of the block.
- Modifier - a possible status of the two previous items.

Lets see how this works by giving you an example:

```html
<ul class="list">
  <li class="list-item active"></li>
  <li class="list-item"></li>
  <li class="list-item"></li>
</ul>
```

```css
.list {}
.list-item {}
.list-item.active {}
```

Then after applying the BEM, we have something like this:

```html
<ul class="list">
  <li class="list__item"></li>
  <li class="list__item"></li>
  <li class="list__item list__item--active"></li>
</ul>
```

```css
.list {}
  .list__item {}
  .list__item--active {}
```

I need to admit that some time ago when I discovered the BEM methodology I thought: “This is weird”. All those __ and -- were strange . But now, that I know more about the idea, I can say that convinced me. Of course, like any others thoughts, there are positive and negative aspects and it is up to you, give the final word.

The benefits of using BEM in my opinion are:

- Easier to reuse components.
- Easy perception of things: looking quickly to the HTML markup or CSS, you can understand what each thing does.

## Sources

- [http://getbem.com/](http://getbem.com/)
