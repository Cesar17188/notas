# Pruebas aisladas al componente

Esto es muy util cuando el componente tiene varios inputs y outputs por lo que estos componentes tienen ese comportamiento necesitan un padre para comprobar que este componente cumple con su función 

person.component.spec.ts
```ts
fdescribe('PersonComponent from HostComponent', () => {
  let component: HostComponent;
  let fixture: ComponentFixture<HostComponent>;

  beforeEach(async () => {
    await TestBed.configureTestingModule({
      declarations: [ HostComponent, PersonComponent ]
    })
    .compileComponents();
  });

  beforeEach(() => {
    fixture = TestBed.createComponent(HostComponent);
    component = fixture.componentInstance;
    fixture.detectChanges();
  });

  it('should create', () => {
    expect(component).toBeTruthy();
  });

  it('should display person name', () => {
    // Arrange
    const expectName = component.person.name;
    const h3De = fixture.debugElement.query(By.css('app-person h3'));
    const h3El = h3De.nativeElement;
    // Act
    fixture.detectChanges();
    // Assert
    expect(h3El.textContent).toContain(expectName);
  });

  it('should raise selected event when do click', () => {
    // Arrange
    const btnDe = fixture.debugElement.query(By.css('app-person .btn-choose'));
    // Act
    btnDe.triggerEventHandler('click', null);
    fixture.detectChanges();
    // Assert
    expect(component.selectedPerson).toEqual(component.person);
  })
})
```