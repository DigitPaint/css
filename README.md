# Digitpaint (S)CSS Style Guide {

*A mostly reasonable approach to CSS and Sass stylesheets*

## <a name='TOC'>Table of Contents</a>

1. [Naming Conventions](#naming-conventions)
1. [Variables](#variables)
1. [Nesting](#nesting)
1. [Extends](#extends)
1. [Includes](#includes)
1. [License](#license)

## <a name='naming-conventions'>Naming conventions</a>

- Use BEM as much as possible (see Harry Robbert's excellend article ["MindBEMding – getting your head ’round BEM syntax"](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) for an introduction)

    ```html
    <!-- bad -->
    <div class="weather header">
      <img src="sunny.png" class="icon">
      <p class="description">Sunny!</p>
    </div>


    <!-- good -->
    <div class="weather weather--header">
      <img src="sunny.png" class="weather__icon">
      <p class="weather__description">Sunny!</p>
    </div>
    ```

## <a name='browser'>Browsers</a>

- Don't do manual vendorprefixing, use a tool like [autoprefixer](https://github.com/ai/autoprefixer) or [prefix-free](http://leaverou.github.io/prefixfree/. 

- Target features, not browsers. Prefer the use of `@supports` if possible, use modernizr otherwise.

- Only target IE < 9 with conditional comments.

## <a name='variables'>Variables</a>

TODO

## <a name='nesting'>Nesting</a>

- Nest based on block name

- Don't mix properties and selectors in a nesting level. Use `&` instead.
  
    ```scss
    // bad
    .weather{
      color: #fff;

      .weather__icon{
        // ...
      }
    }

    // good
    .weather{
      &{
        color: #fff;
      }

      .weather__icon{
        // ...
      }
    }
    ```

- Nest up to a maximum of 2 levels. Too many levels of nesting make especially longer blocks of code unreadable.

    ```scss
    // bad
    .ice-cream{
      .ice-cream__cone{
        .ice-cream__cone__wrapper{
          // ...
        }
      }
    }

    // good
    .ice-cream{
      .ice-cream__cone .ice-cream__cone__wrapper{
         // ...
      }
    }
    ```

- Only point down with the `&` selector in a nesting, never up

    ```scsss
    // bad
    .ice-cream{
      .desert &{
        // ...
      }
    }

    // good
    .desert{
      .ice-cream{

      }
    }

    ```

## <a name='extends'>Extends</a>

- Make abstract extends with `%name` instead of extending actual classes.

    ```scss
    // bad
    .page{
      ...
    }

    .page--home{
      @extend .page;
    }

    // good
    %centered-page{
      ...
    }

    .page{
      @extend %%centered-page;
    }

    .page--home{
      @extend %%centered-page;
    }
    ```

## <a name='includes'>Includes</a>

TODO

## <a name='license'>License</a>

(The MIT License)

Copyright (c) 2014 Digitpaint

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[[⬆]](#TOC)**

# };
