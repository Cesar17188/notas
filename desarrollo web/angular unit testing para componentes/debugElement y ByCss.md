# DebugElement & ByCss

Angular puede correr en diferentes plataformas, pero debugElement y Css puede redenrizarse para poder renderizarse en nativeScript, ademas se puede hacer preview side rendering para lograr un rendirizado previo y agilitar todo el proceso de renderizado.

ahora podemos hacer las pruebas de cálidad del render de una mejor manera

person.component.spec.ts
```ts
it('should have <p> with "Soy un párrafo"</p>', () => {
    const personDebug: DebugElement = fixture.debugElement;
    const pDebug: DebugElement = personDebug.query(By.css('p'));
    const pElement: HTMLElement = pDebug.nativeElement;
    expect(pElement?.textContent).toEqual('Soy un párrafo');
  });

  it('should have <h3> with "Hola, PersonComponent"</h3>', () => {
    const personDebug: DebugElement = fixture.debugElement;
    const h3Debug: DebugElement = personDebug.query(By.css('h3'));
    const h3: HTMLElement = h3Debug.nativeElement;
    expect(h3?.textContent).toEqual('Hola, PersonComponent');
  });
```

Con esto se puede hacer pruebas a los componentes revisando todo el renderizado.