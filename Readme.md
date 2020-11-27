#Validating MVC Applications</br></br>

###Para validación en el propio formulario</br>
**En la clase decoramos los atributos que queremos validar.</br></br>

En este caso queremos validar que sean campos requeridos el first_name y el last_name</br></br>

[Required(ErrorMessage = "Please enter your first name.")]
[Required(ErrorMessage = "Please enter your last name.")]
</br></br>
**En el controlador, que muestra la vista, habrá que controlar que se muestre si los datos son correctos**</br>

<pre><code>
public IActionResult Details(Person person)
      {
        if (!ModelState.IsValid)
        {
            return View("Index", person);
        }
</code></pre>
</br></br>
**En la vista indicamos donde van a salir los errores de validacion.**</br>
En nuestro caso creamos un espacio en la parte superior para que salgan todos los errores de validacion. </br>
Y también por cada elemento</br>
<pre><code>
      <form asp-action="Details">
      <div asp-validation-summary="All"></div>           
            <div class="form-field">
                <label asp-for="FirstName"></label>
                <span class="input-span">
                    <input asp-for="FirstName" />
                <span asp-validation-for="FirstName"></span>
           </div>
            <div class="form-field">
                <label asp-for="LastName"></label>
</code></pre>
