# Componentes en Angular con CSS

![[Pasted image 20211112151626.png]]

Aquí esta el código:

![[Pasted image 20211112172558.png]]

```
div {
  text-align: center;
}

h2 {
  border-bottom: 1.5px solid #6a197d;
  padding-bottom: 10px;
  text-align: center;
}

form {
  background: #e0dede;
  border: 1px solid rgba(106, 25, 125, 0.2);
  border-radius: 10px;
  box-shadow: 5px 3px 5px 1px rgba(0, 0, 0, 0.2);
  margin: 0 50px 25px;
  padding: 10px 25px 25px;
  text-align: center;
  transform: scale(1);
  transition: 0.3s transform;
}

form:hover {
  transform: scale(1.2);
}

button {
  background: #6a197d;
  width: 45px;
  height: 25px;
  border: none;
  border-radius: 10px;
  color: white;
  cursor: pointer;
  transition: border-color 0.15s;
}

button:hover {
  border-color: #ffa5b0;
}

button[disabled] {
  background-color: #f5f5f5;
  color: #6a197d;
  border: 1px solid #6a197d;
}
```