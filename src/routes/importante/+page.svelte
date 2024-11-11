<script>
    import '$lib/css/bootstrap.min.css';
    import '$lib/css/style.css';
    import '$lib/css/importan.css';
    let citasConfirmadas = [];

    function showTab(tab) {
        document.getElementById('pendientes').style.display = 'none';
        document.getElementById('confirmadas').style.display = 'none';
        document.getElementById('calendario').style.display = 'none';
        document.getElementById(tab).style.display = 'block';
    }

    function aceptarCita(nombre, fecha, hora) {
        citasConfirmadas.push({ nombre, fecha, hora });
        alert(`Cita con ${nombre} aceptada`);
        showTab('confirmadas');
        mostrarCitasConfirmadas();
    }

    function rechazarCita(nombre) {
        alert(`Cita con ${nombre} rechazada`);
        // Aquí podrías eliminar la cita de la lista de pendientes si fuera necesario
    }

    function mostrarCitasConfirmadas() {
        const lista = document.getElementById('confirmadas-list');
        lista.innerHTML = '';
        citasConfirmadas.forEach(cita => {
            const card = document.createElement('div');
            card.className = 'card';
            card.innerHTML = `
                <div class="card-header">${cita.nombre}</div>
                <div class="card-body">
                    <p>Fecha: ${cita.fecha}</p>
                    <p>Hora: ${cita.hora}</p>
                </div>
            `;
            lista.appendChild(card);
        });
    }

    function verCita(nombre, fecha, hora) {
        alert(`Cita con ${nombre} para el ${fecha} a las ${hora}`);
    }

    // Mostrar la pestaña de citas pendientes por defecto
    showTab('pendientes');
</script>

<style>
    /* Aquí puedes agregar estilos específicos para el componente en Svelte */
</style>

<main>
    <div class="container">
        <h1>Portal del Psicólogo</h1>
        
        <div class="tabs">
            <button class="tab" on:click={() => showTab('pendientes')} on:keydown={(e) => e.key === 'Enter' || e.key === ' ' ? showTab('pendientes') : null}>
                Citas Pendientes
              </button>
              <button class="tab" on:click={() => showTab('confirmadas')} on:keydown={(e) => e.key === 'Enter' || e.key === ' ' ? showTab('confirmadas') : null}>
                Citas Confirmadas
              </button>
              <button class="tab" on:click={() => showTab('calendario')} on:keydown={(e) => e.key === 'Enter' || e.key === ' ' ? showTab('calendario') : null}>
                Calendario
              </button>
        </div>
    
        <div class="content" id="pendientes">
            <h2>Citas Pendientes</h2>
            <div class="card">
                <div class="card-header">Ana García</div>
                <div class="card-body">
                    <p>Fecha: 24/10/2023</p>
                    <p>Hora: 10:00</p>
                    <button class="btn" on:click={() => aceptarCita('Ana García', '24/10/2023', '10:00')}>Aceptar</button>
                    <button class="btn" on:click={() => rechazarCita('Ana García')}>Rechazar</button>
                </div>
            </div>
            <div class="card">
                <div class="card-header">Carlos Rodríguez</div>
                <div class="card-body">
                    <p>Fecha: 25/10/2023</p>
                    <p>Hora: 14:00</p>
                    <button class="btn" on:click={() => aceptarCita('Carlos Rodríguez', '25/10/2023', '14:00')}>Aceptar</button>
                    <button class="btn" on:click={() => rechazarCita('Carlos Rodríguez')}>Rechazar</button>
                </div>
            </div>
        </div>
    
        <div class="content" id="confirmadas" style="display: none;">
            <h2>Citas Confirmadas</h2>
            <div id="confirmadas-list"></div>
        </div>
    
        <div class="content" id="calendario" style="display: none;">
            <h2>Calendario de Citas</h2>
            <div class="calendar">
                <button class="day today" on:click={() => verCita('Ana García', '24/10/2023', '10:00')} on:keydown={(e) => (e.key === 'Enter' || e.key === ' ') ? verCita('Ana García', '24/10/2023', '10:00') : null}>
                    24<br>Ana García<br><span class="badge">10:00</span>
                  </button>
                  
                  <button class="day" on:click={() => verCita('Carlos Rodríguez', '25/10/2023', '14:00')} on:keydown={(e) => (e.key === 'Enter' || e.key === ' ') ? verCita('Carlos Rodríguez', '25/10/2023', '14:00') : null}>
                    25<br>Carlos Rodríguez<br><span class="badge">14:00</span>
                  </button>                  
                <div class="day">26</div>
                <div class="day">27</div>
                <div class="day">28</div>
                <div class="day">29</div>
                <div class="day">30</div>
            </div>
        </div>
    </div>
</main>

<footer>
    <div class="container-fluid copyright py-4">
        <div class="container">
            <div class="row g-4 align-items-center">
                <div class="col-md-6 text-center text-md-start mb-md-0">
                    <span class="text-white"><a href="1"><i class="fas fa-copyright text-light me-2"></i>You Can Tell
                            Me</a></span>
                </div>
            </div>
        </div>
    </div>
</footer>

<a href="1" aria-label="button" class="btn btn-primary btn-lg-square back-to-top"><i class="fa fa-arrow-up"></i></a>

<!-- JavaScript Libraries -->

