# Explorando matchers
Esperar si esta definido

```
    expect( name ).toBeDefined();
    expect( name2 ).toBeUndefined();
```

Esperar valores booleanos

```
    expect(1 + 3 === 4).toBeTruthy();
    expect(1 + 1 === 3).toBeFalsy();
```

Esperar mayor o menor

```
    expect(5).toBeLessThan(10);
    expect(20).toBeGreaterThan(10);
```

Esperar un match con un regex

```
    expect('123456').toMatch(/123/);
```

Esperar que lo contenga un array

```
    expect(['apples', 'oranges', 'pears']).toContain('oranges');
```

