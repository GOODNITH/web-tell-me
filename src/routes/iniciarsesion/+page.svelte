<script lang="ts">
  import { onMount } from 'svelte';
  import '$lib/css/iniciarsesion.css';

  // Definiendo tipos
  interface HTMLElementWithStyle extends HTMLElement {
      style: CSSStyleDeclaration;
  }

  // Variables reactivas de Svelte
  let formulario_login: HTMLElementWithStyle;
  let formulario_register: HTMLElementWithStyle;
  let contenedor_login_register: HTMLElementWithStyle;
  let caja_trasera_login: HTMLElementWithStyle;
  let caja_trasera_register: HTMLElementWithStyle;
  let wrapper: HTMLElement;

  // Funciones
  const anchoPage = (): void => {
      if (window.innerWidth > 850) {
          caja_trasera_register.style.display = 'block';
          caja_trasera_login.style.display = 'block';
      } else {
          caja_trasera_register.style.display = 'block';
          caja_trasera_register.style.opacity = '1';
          caja_trasera_login.style.display = 'none';
          formulario_login.style.display = 'block';
          formulario_register.style.display = 'none';
          contenedor_login_register.style.left = '0px';
      }
  };

  const iniciarSesion = (): void => {
      if (window.innerWidth > 850) {
          formulario_login.style.display = 'block';
          contenedor_login_register.style.left = '10px';
          formulario_register.style.display = 'none';
          caja_trasera_register.style.opacity = '1';
          caja_trasera_login.style.opacity = '0';
      } else {
          formulario_login.style.display = 'block';
          contenedor_login_register.style.left = '0px';
          formulario_register.style.display = 'none';
          caja_trasera_register.style.display = 'block';
          caja_trasera_login.style.display = 'none';
      }
  };

  const register = (): void => {
      if (window.innerWidth > 850) {
          formulario_register.style.display = 'block';
          contenedor_login_register.style.left = '410px';
          formulario_login.style.display = 'none';
          caja_trasera_register.style.opacity = '0';
          caja_trasera_login.style.opacity = '1';
      } else {
          formulario_register.style.display = 'block';
          contenedor_login_register.style.left = '0px';
          formulario_login.style.display = 'none';
          caja_trasera_register.style.display = 'none';
          caja_trasera_login.style.display = 'block';
          caja_trasera_login.style.opacity = '1';
      }
  };

  const toggleWrapper = (): void => {
      wrapper?.classList.toggle('active');
  };

  // Ciclo de vida de Svelte
  onMount(() => {
      // Asignación de elementos del DOM
      formulario_login = document.querySelector('.formulario__login') as HTMLElementWithStyle;
      formulario_register = document.querySelector('.formulario__register') as HTMLElementWithStyle;
      contenedor_login_register = document.querySelector('.contenedor__login-register') as HTMLElementWithStyle;
      caja_trasera_login = document.querySelector('.caja__trasera-login') as HTMLElementWithStyle;
      caja_trasera_register = document.querySelector('.caja__trasera-register') as HTMLElementWithStyle;
      wrapper = document.querySelector('.wrapper') as HTMLElement;

      // Event listeners
      window.addEventListener('resize', anchoPage);
      document.getElementById('btn__iniciar-sesion')?.addEventListener('click', iniciarSesion);
      document.getElementById('btn__registrarse')?.addEventListener('click', register);
      document.querySelector('.signInBtn-Link')?.addEventListener('click', toggleWrapper);
      document.querySelector('.signUpBtn-Link')?.addEventListener('click', toggleWrapper);

      // Inicialización
      anchoPage();

      // Limpieza de event listeners
      return () => {
          window.removeEventListener('resize', anchoPage);
          document.getElementById('btn__iniciar-sesion')?.removeEventListener('click', iniciarSesion);
          document.getElementById('btn__registrarse')?.removeEventListener('click', register);
          document.querySelector('.signInBtn-Link')?.removeEventListener('click', toggleWrapper);
          document.querySelector('.signUpBtn-Link')?.removeEventListener('click', toggleWrapper);
      };
  });
</script>

<svelte:head>
	<!-- Inicio del encabezado del documento -->
	<meta charset="UTF-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
	<title>You can tell me</title>
	<!-- Título de la página -->

	<link
		href="https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<div class="contenedor__todo">
	<!-- Div contenedor principal -->
	<div class="caja__trasera">
		<!-- Div de la caja trasera -->
		<div class="caja__trasera-login">
			<!-- Div específico para inicio de sesión -->
			<h3>¿Ya tienes una cuenta?</h3>
			<!-- Título de la caja de inicio de sesión -->
			<p>Inicia sesión para entrar en la página</p>
			<!-- Descripción de la caja de inicio de sesión -->
			<button id="btn__iniciar-sesion">Iniciar Sesión</button>
			<!-- Botón para iniciar sesión -->
		</div>
		<div class="caja__trasera-register">
			<!-- Div específico para registro -->
			<h3>¿Aún no tienes una cuenta?</h3>
			<!-- Título de la caja de registro -->
			<p>Regístrate para que puedas iniciar sesión</p>
			<!-- Descripción de la caja de registro -->
			<button id="btn__registrarse">Regístrarse</button>
			<!-- Botón para registrarse -->
		</div>
	</div>

	<!--Formulario de Login y registro-->
	<div class="contenedor__login-register">
		<!-- Div contenedor de formularios de inicio de sesión y registro -->
		<!--Login-->

		<form action="index.html" class="formulario__login" id="loginForm">
			<!-- Formulario de inicio de sesión -->
			<h2>Iniciar Sesión</h2>
			<!-- Título del formulario -->
			<input type="text" placeholder="Correo Electrónico" id="email" />
			<!-- Campo de entrada de correo electrónico -->
			<input type="password" placeholder="Contraseña" id="password" />
			<!-- Campo de entrada de la contraseña -->
			<button type="submit">Entrar</button>
			<!-- Botón para enviar el formulario -->
		</form>

		<!-- Script para validar el formulario de inicio de sesión -->
		<script>
			document.getElementById('loginForm').addEventListener('submit', function (event) {
				var email = document.getElementById('email').value;
				var password = document.getElementById('password').value;

				if (email === '' || password === '') {
					alert('Por favor complete todos los campos');
					event.preventDefault();
				}
			});
		</script>

		<!--Register-->
		<form action="index.html" class="formulario__register" id="registerForm">
			<!-- Formulario de registro -->
			<h2>Regístrarse</h2>
			<!-- Título del formulario -->
			<input type="text" placeholder="Nombre completo" id="fullName" />
			<!-- Campo de entrada de nombre completo -->
			<input type="text" placeholder="Correo Electrónico" id="registerEmail" />
			<!-- Campo de entrada de correo electrónico -->
			<input type="text" placeholder="Usuario" id="username" />
			<!-- Campo de entrada de usuario -->
			<input type="password" placeholder="Contraseña" id="registerPassword" />
			<!-- Campo de entrada de contraseña -->
			<button type="submit">Regístrarse</button>
			<!-- Botón para enviar el formulario -->
		</form>

		<script>
			document.getElementById('registerForm').addEventListener('submit', function (event) {
				var fullName = document.getElementById('fullName').value.trim();
				var email = document.getElementById('registerEmail').value.trim();
				var username = document.getElementById('username').value.trim();
				var password = document.getElementById('registerPassword').value.trim();

				if (fullName === '' || email === '' || username === '' || password === '') {
					alert('Por favor complete todos los campos');
					event.preventDefault();
				}
			});
		</script>
	</div>
</div>
