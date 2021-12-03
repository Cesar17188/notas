# Trabajando en React con Styled Components

![[Pasted image 20211113191031.png]]

**Form:**

```
const StyleForm = styled.form`
  font-family: courier;
  margin: 0 50px 25px;
  padding: 10px 25px 25px;
  text-align: center;
  transform: scale(1);
  transition: transform 0.3s;

  &:hover {
    transform: scale(1.2);
  }
`;
const StyledButton = styled.button`
  cursor: pointer;
  padding: 5px 10px;
  margin: 0px 15px;
  border: 1px solid transparent;
  transition: 0.15s border-color;

  &:hover {
    border-color: blue;
  }

  &[disabled] {
    background: lightblue;
  }
`;
```

**Title**

```
export const Title = style.h2`
    padding-bottom: 10px;
    border-bottom: 1px solid ${(props) => props.theme.color2};
`;
```

### cuidado con typear mal

Estuve como 20min tratando de ver cual era mi error porque me salía en blanco la pantalla y encima la consola no me tiraba ningún error, en micaso era que habia puesto props.childern en vez de children! T.T

```
export const Theme = (props) => (
  <ThemeProvider theme={themes["daredevil"]}>{props.childern}</ThemeProvider>
);

```