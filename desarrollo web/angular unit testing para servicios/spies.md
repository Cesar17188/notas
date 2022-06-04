# Spies

Un Spy permite bloquear o interceptar una funcion y trackear las llamadas a esta y sus argumentos. Estos Spies solo existen en el bloque _describe_ o _it_ en el que fueron definidos, sera removido luego de su implementacion. Podemos definir que hara el Spy luego de ser invocado con and

[jasmine.github.io/tutorials/your_first_suite#section-Spies](https://jasmine.github.io/tutorials/your_first_suite#section-Spies)

master.service.spec.ts
```ts
 it('should call to getValue from ValueService', () => {
    const valueServiceSpy = jasmine.createSpyObj('ValueService', ['getValue']);
    valueServiceSpy.getValue.and.returnValue('fake value');
    const masterService = new MasterService(valueServiceSpy);
    expect(masterService.getValue()).toBe('fake value');
    expect(valueServiceSpy.getValue).toHaveBeenCalled();
    expect(valueServiceSpy.getValue).toHaveBeenCalledTimes(1);
  });
```



Mocking

> Son objetos simulados (pseudo-objetos, mock object, objetos de pega) a los que imitan el comportamiento de objetos reales de una forma controlada