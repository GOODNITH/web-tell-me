<script lang="ts">
	import { onMount } from 'svelte';

	onMount(() => {
		const jqueryScript: HTMLScriptElement = document.createElement('script');
		jqueryScript.src = 'https://ajax.googleapis.com/ajax/libs/jquery/3.6.4/jquery.min.js';
		document.body.appendChild(jqueryScript);

		const bootstrapScript: HTMLScriptElement = document.createElement('script');
		bootstrapScript.src =
			'https://cdn.jsdelivr.net/npm/bootstrap@5.0.0/dist/js/bootstrap.bundle.min.js';
		document.body.appendChild(bootstrapScript);
	});

	const spinner = (): void => {
		setTimeout((): void => {
			const spinnerElement = document.getElementById('spinner');
			if (spinnerElement) {
				spinnerElement.classList.remove('show');
			}
		}, 1);
	};

	spinner();

	// Header Carousel Configuration
	const initHeaderCarousel = (): void => {
		const headerCarousel = document.querySelector('.header-carousel') as HTMLElement;
		if (headerCarousel) {
			new (window as any).Owl(headerCarousel, {
				animateOut: 'slideOutDown',
				items: 1,
				autoplay: true,
				smartSpeed: 1000,
				dots: false,
				loop: true,
				nav: true,
				navText: ['<i class="bi bi-arrow-left"></i>', '<i class="bi bi-arrow-right"></i>']
			});
		}
	};

	// Testimonial Carousel Configuration
	const initTestimonialCarousel = (): void => {
		const testimonialCarousel = document.querySelector('.testimonial-carousel') as HTMLElement;
		if (testimonialCarousel) {
			new (window as any).Owl(testimonialCarousel, {
				autoplay: true,
				items: 1,
				smartSpeed: 1500,
				dots: true,
				dotsData: true,
				loop: true,
				margin: 25,
				nav: true,
				navText: ['<i class="bi bi-arrow-left"></i>', '<i class="bi bi-arrow-right"></i>']
			});
		}
	};

	// Back to top functionality
	const initBackToTop = (): void => {
		const backToTop = document.querySelector('.back-to-top') as HTMLElement;
		if (!backToTop) return;

		window.addEventListener('scroll', (): void => {
			if (window.scrollY > 300) {
				backToTop.style.display = 'block';
				backToTop.style.opacity = '1';
				backToTop.style.transition = 'opacity 0.3s ease-in-out';
			} else {
				backToTop.style.opacity = '0';
				setTimeout(() => {
					backToTop.style.display = 'none';
				}, 300);
			}
		});

		backToTop.addEventListener('click', (e: Event): void => {
			e.preventDefault();
			window.scrollTo({
				top: 0,
				behavior: 'smooth'
			});
		});
	};

	// Initialize all components
	const initializeComponents = (): void => {
		spinner();
		initHeaderCarousel();
		initTestimonialCarousel();
		initBackToTop();
	};

	// Run initialization when DOM is ready
	document.addEventListener('DOMContentLoaded', initializeComponents);
</script>

<svelte:head>
	<meta charset="utf-8" />
	<title>You Can Tell Me</title>
	<meta content="width=device-width, initial-scale=1.0" name="viewport" />
	<meta content="" name="keywords" />
	<meta content="" name="description" />

	<!-- Google Web Fonts -->
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="" />
	<link
		href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@500;600;700&family=Rubik:wght@400;500&display=swap"
		rel="stylesheet"
	/>

	<!-- Icon Font Stylesheet -->
	<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.15.4/css/all.css" />
	<link
		href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.4.1/font/bootstrap-icons.css"
		rel="stylesheet"
	/>

	<!-- Libraries Stylesheet -->
	<link href="lib/animate/animate.min.css" rel="stylesheet" />
	<link href="lib/owlcarousel/assets/owl.carousel.min.css" rel="stylesheet" />
	<link href="lib/lightbox/css/lightbox.min.css" rel="stylesheet" />

	<!-- Customized Bootstrap Stylesheet -->
	<link href="css/bootstrap.min.css" rel="stylesheet" />

	<!-- Template Stylesheet -->
	<link href="css/style.css" rel="stylesheet" />
</svelte:head>

<!-- Spinner Start -->
<div
	id="spinner"
	class="show bg-white position-fixed translate-middle w-100 vh-100 top-50 start-50 d-flex align-items-center justify-content-center"
>
	<div class="spinner-border text-primary" style="width: 3rem; height: 3rem;" role="status">
		<span class="sr-only">Loading...</span>
	</div>
</div>
<!-- Spinner End -->

<!-- Navbar & Hero Start -->
<div class="container-fluid header position-relative overflow-hidden p-0">
	<nav class="navbar navbar-expand-lg fixed-top navbar-light px-4 px-lg-5 py-3 py-lg-0">
		<a href="index.html" class="navbar-brand p-0">
			<h1 class="display-6 text-primary m-0">
				<img src="img/una-mariposa-de-lado.png" alt="Logo" style="width: 80px; height: auto;" /> You
				can tell me
			</h1>
		</a>
		<button
			class="navbar-toggler"
			type="button"
			data-bs-toggle="collapse"
			data-bs-target="#navbarCollapse"
			aria-label="Toggle navigation"
		>
			<span class="fa fa-bars"></span>
		</button>
		<div class="collapse navbar-collapse" id="navbarCollapse">
			<div class="navbar-nav ms-auto py-0">
				<a href="index.html" class="nav-item nav-link active">Inicio</a>
				<a href="citasssssssssssssssss.html" class="nav-item nav-link">CITAS</a>
				<a href="importante.html" class="nav-item nav-link">Crear citas</a>
				<div class="nav-item dropdown">
					<button class="nav-link dropdown-toggle" data-bs-toggle="dropdown" type="button">Paginas</button>
					<div class="dropdown-menu m-0">
						<a href="sobrenosotras.html" class="dropdown-item active">Sobre Nosotros</a>
						<a href="EstrategiasDMDE.html" class="dropdown-item">Estrategias de Manejo del Estrés</a
						>
						<a href="Tecnicasderelajacion.html" class="dropdown-item">Técnicas de Relajación </a>
					</div>
				</div>
				<a href="contact.html" class="nav-item nav-link">Contáctanos</a>
			</div>
		</div>
	</nav>

	<!-- Hero Header Start -->
	<div class="hero-header overflow-hidden px-5">
		<div class="rotate-img">
			<img src="img/sty-1.png" class="img-fluid w-100" alt="" />
			<div class="rotate-sty-2"></div>
		</div>
		<div class="row gy-5 align-items-center">
			<div class="col-lg-6 wow fadeInLeft" data-wow-delay="0.1s">
				<h1 class="display-4 text-dark mb-4 wow fadeInUp" data-wow-delay="0.3s">
					Enfrenta los Retos Estudiantiles con Confianza
				</h1>
				<p class="fs-4 mb-4 wow fadeInUp" data-wow-delay="0.5s">
					Aprende a gestionar la ansiedad y el estrés académico con técnicas basadas en psicología.
					Con nuestro apoyo, podrás enfrentar los desafíos estudiantiles con confianza y mejorar tu
					rendimiento.
				</p>
				<a
					href="EstrategiasDMDE.html"
					class="btn btn-primary rounded-pill py-3 px-5 wow fadeInUp"
					data-wow-delay="0.7s">Explora Recursos</a
				>
			</div>
			<div class="col-lg-6 wow fadeInRight" data-wow-delay="0.2s">
				<img src="img/NS.png" class="img-fluid w-100 h-100" alt="" />
			</div>
		</div>
	</div>
	<!-- Hero Header End -->
</div>
<!-- Navbar & Hero End -->

<!-- About Start -->
<div class="container-fluid overflow-hidden py-5" style="margin-top: 6rem;">
	<div class="container py-5">
		<div class="row g-5">
			<div class="col-lg-6 wow fadeInUp" data-wow-delay="0.1s">
				<div class="RotateMoveLeft">
					<img
						src="img/apoyo-psicol-gico-adaptado-a-estudiantes.png"
						class="img-fluid w-100"
						alt=""
					/>
				</div>
			</div>
			<div class="col-lg-6 wow fadeInUp" data-wow-delay="0.3s">
				<h4 class="mb-1 text-primary">Sobre Nosotros</h4>
				<h1 class="display-5 mb-4">Apoyo Psicológico Adaptado a Estudiantes</h1>
				<p class="mb-4">
					Ofrecemos herramientas y apoyo psicológico especializado para estudiantes. Nuestro
					objetivo es ayudarte a manejar el estrés, mejorar tu bienestar emocional y potenciar tu
					rendimiento académico.
				</p>
				<a href="sobrenosotros.html" class="btn btn-primary rounded-pill py-3 px-5">Saber Más</a>
			</div>
		</div>
	</div>
</div>
<!-- About End -->

<!-- servicios inicio -->
<div class="container-fluid feature overflow-hidden py-5">
	<div class="container py-5">
		<div
			class="text-center mx-auto mb-5 wow fadeInUp"
			data-wow-delay="0.1s"
			style="max-width: 900px;"
		>
			<h4 class="text-primary">Nuestras Características</h4>
			<h1 class="display-5 mb-4">
				Características Importantes para el Apoyo Psicológico Estudiantil
			</h1>
			<p class="mb-0">
				Descubre cómo nuestras herramientas y recursos especializados pueden ayudarte a manejar el
				estrés académico, mejorar tu bienestar emocional y lograr un equilibrio durante tus
				estudios. Nuestro enfoque está diseñado para brindarte el apoyo que necesitas en cada paso
				de tu formación.
			</p>
		</div>
		<div class="row g-4 justify-content-center text-center mb-5">
			<div class="col-md-6 col-lg-4 col-xl-3 wow fadeInUp" data-wow-delay="0.1s">
				<div class="text-center p-4">
					<div class="d-inline-block rounded bg-light p-4 mb-4">
						<i class="fas fa-brain fa-5x text-secondary"></i>
					</div>
					<div class="feature-content">
						<!-- svelte-ignore a11y_invalid_attribute -->
						<a href="#" class="h4">Apoyo Psicológico <i class="fa fa-long-arrow-alt-right"></i></a>
						<p class="mt-4 mb-0">Orientación y asesoramiento personalizado para estudiantes.</p>
					</div>
				</div>
			</div>
			<div class="col-md-6 col-lg-4 col-xl-3 wow fadeInUp" data-wow-delay="0.3s">
				<div class="text-center p-4">
					<div class="d-inline-block rounded bg-light p-4 mb-4">
						<i class="fas fa-medkit fa-5x text-secondary"></i>
					</div>
					<div class="feature-content">
						<a href="EstrategiasDMDE.html" class="h4"
							>Estrategias de Manejo del Estrés <i class="fa fa-long-arrow-alt-right"></i></a
						>
						<p class="mt-4 mb-0">
							Aprende a gestionar el estrés con técnicas eficaces y prácticas.
						</p>
					</div>
				</div>
			</div>
			<div class="col-md-6 col-lg-4 col-xl-3 wow fadeInUp" data-wow-delay="0.5s">
				<div class="text-center rounded p-4">
					<div class="d-inline-block rounded bg-light p-4 mb-4">
						<i class="fas fa-spa fa-5x text-secondary"></i>
					</div>
					<div class="feature-content">
						<a href="Tecnicasderelajacion.html" class="h4"
							>Técnicas de Relajación <i class="fa fa-long-arrow-alt-right"></i></a
						>
						<p class="mt-4 mb-0">
							Prácticas y herramientas para calmar la mente y reducir la ansiedad.
						</p>
					</div>
				</div>
			</div>
			<div class="col-md-6 col-lg-4 col-xl-3 wow fadeInUp" data-wow-delay="0.7s">
				<div class="text-center rounded p-4">
					<div class="d-inline-block rounded bg-light p-4 mb-4">
						<i class="fas fa-graduation-cap fa-5x text-secondary"></i>
					</div>
					<div class="feature-content">
						<!-- svelte-ignore a11y_invalid_attribute -->
						<a href="#" class="h4">Apoyo Académico <i class="fa fa-long-arrow-alt-right"></i></a>
						<p class="mt-4 mb-0">
							Técnicas para mejorar la concentración y el rendimiento académico.
						</p>
					</div>
				</div>
			</div>
		</div>
		<div class="row g-5 pt-5" style="margin-top: 6rem;">
			<div class="col-lg-6 wow fadeInLeft" data-wow-delay="0.1s">
				<div class="feature-img RotateMoveLeft h-100" style="object-fit: cover;">
					<div class="img-fluid w-100 h-100">
						<img src="img/features-1.png" class="w-100 h-100" alt="" style="object-fit: contain;" />
					</div>
				</div>
			</div>
		</div>
	</div>
	<!-- servicios fin -->

	<!-- FAQ Start -->
	<div class="container-fluid FAQ bg-light overflow-hidden py-5">
		<div class="container py-5">
			<div class="row g-5 align-items-center">
				<div class="col-lg-6 wow fadeInLeft" data-wow-delay="0.1s">
					<div class="accordion" id="accordionExample">
						<div class="accordion-item border-0 mb-4">
							<h2 class="accordion-header" id="headingOne">
								<button
									class="accordion-button rounded-top"
									type="button"
									data-bs-toggle="collapse"
									data-bs-target="#collapseOne"
									aria-expanded="true"
									aria-controls="collapseTOne"
								>
									¿Por que elejir nuestros servicios?
								</button>
							</h2>
							<div
								id="collapseOne"
								class="accordion-collapse collapse show"
								aria-labelledby="headingOne"
								data-bs-parent="#accordionExample"
							>
								<div class="accordion-body my-2">
									<h5>¿Por que elejirnos?</h5>
									<p>
										podemos ofrecer varios beneficios significativos, especialmente si estás
										buscando apoyo, información o recursos para manejar desafíos, esta pagina esta
										dedicada a la salud mental proporcionan información basada en evidencia sobre la
										depresión y la ansiedad, lo que te ayuda a entender mejor estas condiciones,
										además ofrecemos herramientas y recursos de autoayuda, como guías, ejercicios y
										técnicas de manejo del estrés que puedes aplicar en tu vida diaria.
									</p>
									<p>
										acilitamos el acceso a profesionales de la salud mental, permitiéndote buscar
										terapia o asesoramiento en línea.
									</p>
								</div>
							</div>
						</div>
						<div class="accordion-item border-0 mb-4">
							<h2 class="accordion-header" id="headingTwo">
								<button
									class="accordion-button collapsed rounded-top"
									type="button"
									data-bs-toggle="collapse"
									data-bs-target="#collapseTwo"
									aria-expanded="false"
									aria-controls="collapseTwo"
								>
									Conexion con profesionales
								</button>
							</h2>
							<div
								id="collapseTwo"
								class="accordion-collapse collapse"
								aria-labelledby="headingTwo"
								data-bs-parent="#accordionExample"
							>
								<div class="accordion-body my-2">
									<h5>Servicio de Psicología Escolar</h5>
									<p>
										En la I.E,Carlos Vieco Ortiz , nos comprometemos a apoyar el bienestar emocional
										y académico de nuestros estudiantes a través de nuestro dedicado Servicio de
										Psicología Escolar. Este servicio está diseñado para ayudar a los estudiantes a
										enfrentar los desafíos personales y académicos, promoviendo un ambiente escolar
										saludable y positivo.
									</p>
									<p>
										Nuestro servicio de psicología contribuye significativamente al desarrollo
										personal y académico de los estudiantes. Ofrecemos apoyo para manejar el estrés,
										mejorar las habilidades sociales y fomentar la resiliencia emocional, asegurando
										que cada estudiante tenga las herramientas necesarias para alcanzar su máximo
										potencial
									</p>
								</div>
							</div>
						</div>
						<div class="accordion-item border-0">
							<h2 class="accordion-header" id="headingThree">
								<button
									class="accordion-button collapsed rounded-top"
									type="button"
									data-bs-toggle="collapse"
									data-bs-target="#collapseThree"
									aria-expanded="false"
									aria-controls="collapseThree"
								>
									¿Que pasa con su información?
								</button>
							</h2>
							<div
								id="collapseThree"
								class="accordion-collapse collapse"
								aria-labelledby="headingThree"
								data-bs-parent="#accordionExample"
							>
								<div class="accordion-body my-2">
									<h5>Protección de Datos</h5>
									<p>
										limitaremos el acceso a la información de las citas solo a las personas que
										realmente lo necesiten, como el psicólogo y el personal administrativo
										autorizado, además de tener el consentimiento explícito de los usuarios para
										recopilar y utilizar su información personal. Proporcionar una información clara
										sobre cómo se manejarán sus datos.
									</p>
									<p>
										Capacitar a nuestro personal sobre la importancia de la privacidad y la
										seguridad de los datos, y sobre cómo manejar la información de manera segura y
										confidencial.
									</p>
								</div>
							</div>
						</div>
					</div>
				</div>
				<div class="col-lg-6 wow fadeInRight" data-wow-delay="0.3s">
					<div class="FAQ-img RotateMoveRight rounded">
						<img
							src="img/una-persona-en-una-cita-con-su-psicologa--servicio.jpg"
							class="img-fluid w-100"
							alt=""
						/>
					</div>
				</div>
			</div>
		</div>
	</div>
	<!-- FAQ End -->

	<!-- aca va lo que les mande el 9/10/2024 alas9:26-->

	<!-- Footer Inicio -->
	<div class="container-fluid footer py-5 wow fadeIn" data-wow-delay="0.2s">
		<div class="container py-5">
			<div class="row g-5 justify-content-center text-center">
				<div class="col-md-6 col-lg-6 col-xl-3">
					<div class="footer-item d-flex flex-column">
						<h4 class="text-dark mb-4">Proyecto</h4>
						<a href="servicios.html"> Nuestros Servicios</a>
						<a href="sobrenosotros.html"> Sobre Nosotros</a>
					</div>
				</div>
				<div class="col-md-6 col-lg-6 col-xl-3">
					<div class="footer-item d-flex flex-column">
						<h4 class="mb-4 text-dark">Enlaces Rápidos</h4>
						<a href="contact.html"> Contáctanos</a>
						<!-- svelte-ignore a11y_invalid_attribute -->
						<a href=""> Política de Privacidad</a>
						<!-- svelte-ignore a11y_invalid_attribute -->
						<a href=""> Términos y Condiciones</a>
					</div>
				</div>
				<div class="col-md-6 col-lg-6 col-xl-3">
					<div class="footer-item d-flex flex-column">
						<h4 class="mb-4 text-dark">Servicios</h4>
						<a href="EstrategiasDMDE.html"> Estrategias de Manejo del Estrés</a>
						<a href="Tecnicasderelajacion.html"> Técnicas de Relajación</a>
						<!-- svelte-ignore a11y_invalid_attribute -->
						<a href=""> Apoyo Académico</a>
					</div>
				</div>
				<div class="col-md-6 col-lg-6 col-xl-3">
					<div class="footer-item d-flex flex-column">
						<h4 class="mb-4 text-dark">Información de Contacto</h4>
						<!-- svelte-ignore a11y_invalid_attribute -->
						<a href=""><i class="fas fa-envelope me-2"></i> cardonavalenciasara@gmail.com</a>
						<!-- svelte-ignore a11y_invalid_attribute -->
						<a href=""><i class="fas fa-phone me-2"></i> 3239690101</a>
						<!-- svelte-ignore a11y_invalid_attribute -->
						<a href="" class="mb-3"><i class="fas fa-print me-2"></i> 3229633103</a>
						<div class="d-flex justify-content-center align-items-center">
							<i class="fas fa-share fa-2x text-secondary me-2"></i>

						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
	<!-- Footer Fin -->

	<!-- Copyright Start -->
	<div class="container-fluid copyright py-4">
		<div class="container">
			<div class="row g-4 align-items-center">
				<div class="col-md-6 text-center text-md-start mb-md-0">
					<span class="text-white">
						<span class="d-inline-block">
							<i class="fas fa-copyright text-light me-2"></i>You Can Tell Me
						</span>, All rights reserved.
					</span>
				</div>
				<div class="col-md-6 text-center text-md-end text-white">
					Designed by <span class="border-bottom">You Can Tell Me Team</span> | Distributed with care.
				</div>
			</div>
		</div>
	</div>
	<!-- Copyright End -->

	<!-- Back to Top -->
	<a href="#top" class="btn btn-primary btn-lg-square back-to-top" aria-label="Volver arriba">
		<i class="fa fa-arrow-up"></i>
	</a>
</div>
