{% extends './base.html' %}

{% block title %}Login{% endblock %}

{% block customCSS %}
<link rel="stylesheet" href="{{ url_for('static', filename='css/login.css')}}">
{% endblock %}


{% block body %}

<form class="form-signin" action="/login" method="POST">
    <img class="mb-4" src="{{ url_for('static', filename='img/hotel.jpeg') }}" alt="" width="200" height="200">
    {% with messages = get_flashed_messages() %}

    {% if messages %}
    {% for message in messages %}
    <br/>
    <div class="alert alert-primary alert-dismissible" role="alert">
      <strong>{{ message }}</strong>
      <button type="button" class="btn-close" data-bs-dismiss="alert" aria-label="Close"></button>

    </div>
    {% endfor %}    
    {% endif %}

    {% endwith %}
    <h1 class="h3 mb-3 fw-normal">Por favor ingrese:</h1>
    <div class="form-floating">
      <input type="text" class="form-control" id="username" name="username" placeholder="Usuario">
      <label for="username">Usuario</label>
    </div>
    <div class="form-floating mt-2">
      <input type="password" class="form-control" name="password" placeholder="Contraseña">
      <label for="password">Contraseña</label>
    </div>
    <button class="w-100 btn btn-lg btn-primary" type="submit">Iniciar Sesión</button>
  </form>
{% endblock %}
