# Setup y maquetación del proyecto

Lo primero antes de hacer pruebas a las conexiones http con conexiones a API's sera crear nuestro setup.

Para ello lo primero sera instalar un framework minimalista de diseño que tenga precargado las etiquetas html pero que no sea tan pesado. Por lo que no se tendra que pensar en clases como por ejemplo [miligram](https://milligram.io/)
o [simple.css](https://simplecss.org/) o [pico.css](https://picocss.com/)

Para este ejemplo usaremos [pico.css](https://picocss.com/)

lo instalamos
```
npm install @picocss/pico
```

una vez instalado vamos al nodemodules, buscamos la carpeta de @picocss/pico/css y buscamos el archivo pico.min.css, damos clic derecho y copiamos su ruta relativa.

despues vamos al archivo angular.json y lo pegamos en la reglas styles

```json
"options": {
            "styles": [
              "src/styles.scss",
              "node_modules/@picocss/pico/css/pico.min.css"
            ],
            "scripts": []
          },
```

con estos cambios vamos a reescribir la landing page de nuestra aplicación

app.component.html
```html
<header class="container">
  <h1>Angular Testing</h1>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Beatae illum saepe odio suscipit id sapiente consequuntur, ipsa laboriosam eius debitis quidem nisi quos veritatis eum soluta adipisci repellat commodi. Esse.</p>
  <nav>
    <ul>
      <li><a href="/">Home</a></li>
      <li><a routerLink="/products">Products</a></li>
      <li><a routerLink="/pico-preview">Pico Preview</a></li>
    </ul>
  </nav>
</header>
<router-outlet></router-outlet>
```

posteriormente creamos la carpeta components con dos componentes el de produts y el de pico-preview

```
ng g c components/products

ng g c components/pico-preview
```

y vamos a hacer un routing a estos componentes para verlos renderizados

app-routing.module.ts
```ts
import { ProductsComponent } from './components/products/products.component';
import { PicoPreviewComponent } from './components/pico-preview/pico-preview.component';

const routes: Routes = [
  {
    path: 'products',
    component: ProductsComponent
  },
  {
    path: 'pico-preview',
    component: PicoPreviewComponent
  }
];

```

luego modelamos los componentes de products y preview

products.component.html
```html
<section class="container">
  <h1>Products Component</h1>
</section>
```

preview.component.html
```html
<!-- preview -->
<section id="preview" class="container">
  <h2>Preview</h2>
  <p>Sed ultricies dolor non ante vulputate hendrerit. Vivamus sit amet suscipit sapien. Nulla iaculis eros a elit pharetra egestas.</p>
  <form>
    <div class="grid">
      <input type="text" name="firstnane" placeholder="First name" aria-label="First name" required>
      <input type="email" name="email" placeholder="Email address" aria-label="Email address" required>
      <button type="submit">Subscribe</button>
    </div>
    <fieldset>
      <label for="terms">
        <input type="checkbox" role="switch" id="terms" name="terms">
        <span>I agree to the <a href="#" onclick="event.preventDefault()">Privacy Policy</a></span>
      </label>
    </fieldset>
  </form>
</section>
<!-- ./ Preview -->
<!-- Typografy -->
<section id="typografy" class="container">
  <h2>Typografy</h2>
  <p>Aliquam lobortis vitae nibh nec rhoncus. Morbi mattis neque eget efficitur feugiat. Vivamus porta nunc a erat mattis, mattis feugiat turpis pretium. Quisque sed tristique felis.</p>
  <!-- Blockquote -->
  <blockquote>
    Maecenas vehicula metus tellus, vitae congue turpis hendrerit non. Nam at dui sit amet ipsum cursus ornare.
    <footer>
      <cite> - Phasellus eget lacinia </cite>
    </footer>
  </blockquote>
  <!-- Lists -->
  <h3>Lists</h3>
  <ul>
    <li>
      Aliquam lobortis lacus eu libero ornare facilisis.
    </li>
    <li>
      Nam et magna at libero scelerisque egestas.
    </li>
    <li>
      Suspendisse id nisl ut leo finibus vehicula quis eu ex.
    </li>
    <li>
      Proin ultricies turpis et volutpat vehicula.
    </li>
  </ul>
  <!-- Inline text elements -->
  <h3>Inline text elements</h3>
  <div class="grid">
    <p>
      <a href="#" onclick="event.preventDefault()">Primary Link</a>
    </p>
    <p>
      <a href="#" class="secondary" onclick="event.preventDefault()">Secondary Link</a>
    </p>
    <p>
      <a href="#" class="contrast" onclick="event.preventDefault()">Contrast Link</a>
    </p>
  </div>
  <div class="grid">
    <p>
      <strong>Bold</strong>
    </p>
    <p>
      <em>Italic</em>
    </p>
    <p>
      <u>Underline</u>
    </p>
  </div>
  <div class="grid">
    <p>
      <del>Deleted</del>
    </p>
    <p>
      <ins>Inserted</ins>
    </p>
    <p>
      <s>Strikethrough</s>
    </p>
  </div>
  <div class="grid">
    <p>
      <small>Small</small>
    </p>
    <p>
      Text
      <sub>Sub</sub>
    </p>
    <p>
      Text
      <sup>Sup</sup>
    </p>
  </div>
  <div class="grid">
    <p>
      <abbr title="Abbreviation" data-tooltip="Abbreviation">Abbr</abbr>
    </p>
    <p>
      <kbd>Kdb</kbd>
    </p>
    <p>
      <mark>Highlighted</mark>
    </p>
  </div>
  <!-- Heading -->
  <h3>Heading 3</h3>
  <p>
    Integer bibendum malesuada libero vel eleifend. Fusce iaculis turpis ipsum, at efficitur sem scelerisque vel. Aliquam auctor diam ut purus cursus fringilla. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos.
  </p>
  <h4>Heading 4</h4>
  <p>
    Cras fermentum velit vitae auctor aliquet. Nunc non congue urna, at blandit nibh. Donec ac fermentum felis. Vivamus tincidunt arcu ut lacus hendrerit, eget mattis dui finibus.
  </p>
  <h5>Heading 5</h5>
  <p>
    Donec nec egestas nulla. Sed varius placerat felis eu suscipit. Mauris maximus ante in consequat luctus. Morbi euismod sagittis efficitur. Aenean non eros orci. Vivamus ut diam sem.
  </p>
  <h6>Heading 6</h6>
  <p>
    Ut sed quam non mauris placerat consequat vitae id risus. Vestibulum tincidunt nulla ut tortor posuere, vitae malesuada tortor molestie. Sed nec interdum dolor. Vestibulum id auctor nisi, a efficitur sem. Aliquam sollicitudin efficitur turpis, sollicitudin hendrerit ligula semper id. Nunc risus felis, egestas eu tristique eget, convallis in velit.
  </p>
  <!-- Medias -->
  <figure>
    <img src="https://source.unsplash.com/a562ZEFKW8I/2000x1000" alt="Minimal landscape">

    <figcaption>

      Image from

      <a href="https://unsplash.com">unsplash.com</a>

    </figcaption>

  </figure>

</section>

<!-- ./ Typografy -->

<!-- Buttons -->

<section class="container" id="buttons">

  <h2>Buttons</h2>

  <div class="grid">

    <button>Primary</button>

    <button class="secondary">Secondary</button>

    <button class="contrat">Contrast</button>

  </div>

  <div class="grid">

    <button class="outline">Primary outline</button>

    <button class="outline secondary">Secondary outline</button>

    <button class="outline contrast">Contrast outline</button>

  </div>

</section>

<!-- ./ Buttons -->

<!-- Form elements -->

<section id="form" class="container">

  <form>

    <h2>Form elements</h2>

    <!-- Search -->

    <label for="search">Search</label>

    <input type="search" id="search" name="search" placeholder="Search">

    <!-- Text -->

    <label for="text">Text</label>

    <input type="text" id="text" name="text" placeholder="Text">

    <small>Curabitur consequat lacus at lacus porta finibus.</small>

    <!-- Select -->

    <label for="select">Select</label>

    <select name="select" id="select" required>

      <option value selected>Select...</option>

      <option>...</option>

    </select>

    <!-- File browser -->

    <label for="file">

      File browser

      <input type="file" id="file" name="file">

    </label>

    <!-- Range slider control -->

    <label for="range">

      Range slider

      <input type="range" min="0" max="100" value="50" id="range" name="range">

    </label>

    <!-- States -->

    <div class="grid">

      <label for="valid">

        Valid

        <input

          type="text"

          id="valid"

          name="valid"

          placeholder="Valid"

          aria-invalid="false"

        />

      </label>

      <label for="invalid">

        Invalid

        <input

          type="text"

          id="invalid"

          name="invalid"

          placeholder="Invalid"

          aria-invalid="true"

        />

      </label>

      <label for="disabled">

        Disabled

        <input

          type="text"

          id="disabled"

          name="disabled"

          placeholder="Disabled"

          disabled

        />

      </label>

    </div>

  

    <div class="grid">

      <!-- Date-->

      <label for="date"

        >Date

        <input type="date" id="date" name="date" />

      </label>

  

      <!-- Time-->

      <label for="time"

        >Time

        <input type="time" id="time" name="time" />

      </label>

  

      <!-- Color-->

      <label for="color"

        >Color

        <input type="color" id="color" name="color" value="#0eaaaa" />

      </label>

    </div>

  

    <div class="grid">

      <!-- Checkboxes -->

      <fieldset>

        <legend><strong>Checkboxes</strong></legend>

        <label for="checkbox-1">

          <input type="checkbox" id="checkbox-1" name="checkbox-1" checked />

          Checkbox

        </label>

        <label for="checkbox-2">

          <input type="checkbox" id="checkbox-2" name="checkbox-2" />

          Checkbox

        </label>

      </fieldset>

  

      <!-- Radio buttons -->

      <fieldset>

        <legend><strong>Radio buttons</strong></legend>

        <label for="radio-1">

          <input

            type="radio"

            id="radio-1"

            name="radio"

            value="radio-1"

            checked

          />

          Radio button

        </label>

        <label for="radio-2">

          <input type="radio" id="radio-2" name="radio" value="radio-2" />

          Radio button

        </label>

      </fieldset>

  

      <!-- Switch -->

      <fieldset>

        <legend><strong>Switches</strong></legend>

        <label for="switch-1">

          <input

            type="checkbox"

            id="switch-1"

            name="switch-1"

            role="switch"

            checked

          />

          Switch

        </label>

        <label for="switch-2">

          <input

            type="checkbox"

            id="switch-2"

            name="switch-2"

            role="switch"

          />

          Switch

        </label>

      </fieldset>

    </div>

  

    <!-- Buttons -->

    <input type="reset" value="Reset" onclick="event.preventDefault()" />

    <input type="submit" value="Submit" onclick="event.preventDefault()" />

  </form>

</section>

<!-- ./ Form elements-->

  

<!-- Tables -->

<section id="tables">

  <h2>Tables</h2>

  <figure>

    <table role="grid">

      <thead>

        <tr>

          <th scope="col">#</th>

          <th scope="col">Heading</th>

          <th scope="col">Heading</th>

          <th scope="col">Heading</th>

          <th scope="col">Heading</th>

          <th scope="col">Heading</th>

          <th scope="col">Heading</th>

          <th scope="col">Heading</th>

        </tr>

      </thead>

      <tbody>

        <tr>

          <th scope="row">1</th>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

        </tr>

        <tr>

          <th scope="row">2</th>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

        </tr>

        <tr>

          <th scope="row">3</th>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

          <td>Cell</td>

        </tr>

      </tbody>

    </table>

  </figure>

</section>

<!-- ./ Tables -->

  

<!-- Accordions -->

<section id="accordions">

  <h2>Accordions</h2>

  <details>

    <summary>Collapsible elements 1</summary>

    <p>

      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque

      urna diam, tincidunt nec porta sed, auctor id velit. Etiam venenatis

      nisl ut orci consequat, vitae tempus quam commodo. Nulla non mauris

      ipsum. Aliquam eu posuere orci. Nulla convallis lectus rutrum quam

      hendrerit, in facilisis elit sollicitudin. Mauris pulvinar pulvinar mi,

      dictum tristique elit auctor quis. Maecenas ac ipsum ultrices, porta

      turpis sit amet, congue turpis.

    </p>

  </details>

  <details open>

    <summary>Collapsible elements 2</summary>

    <ul>

      <li>Vestibulum id elit quis massa interdum sodales.</li>

      <li>Nunc quis eros vel odio pretium tincidunt nec quis neque.</li>

      <li>Quisque sed eros non eros ornare elementum.</li>

      <li>Cras sed libero aliquet, porta dolor quis, dapibus ipsum.</li>

    </ul>

  </details>

</section>

<!-- ./ Accordions -->

  

<!-- Article-->

<article id="article">

  <h2>Article</h2>

  <p>

    Nullam dui arcu, malesuada et sodales eu, efficitur vitae dolor. Sed

    ultricies dolor non ante vulputate hendrerit. Vivamus sit amet suscipit

    sapien. Nulla iaculis eros a elit pharetra egestas. Nunc placerat

    facilisis cursus. Sed vestibulum metus eget dolor pharetra rutrum.

  </p>

  <footer>

    <small>Duis nec elit placerat, suscipit nibh quis, finibus neque.</small>

  </footer>

</article>

<!-- ./ Article-->

  

<!-- Progress -->

<section id="progress">

  <h2>Progress bar</h2>

  <progress id="progress-1" value="25" max="100"></progress>

  <progress id="progress-2"></progress>

</section>

<!-- ./ Progress -->

  

<!-- Loading -->

<section id="loading">

  <h2>Loading</h2>

  <article aria-busy="true"></article>

  <button aria-busy="true">Please wait…</button>

</section>

<!-- ./ Loading -->

<!-- Footer -->

<footer class="container">

<small

  >Built with <a href="https://picocss.com">Pico</a> •

  <a href="https://github.com/picocss/examples/blob/master/preview/index.html"

    >Source code</a

  ></small

>

</footer>

<!-- ./ Footer -->
```