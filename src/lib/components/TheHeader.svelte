<script>
    import profilePicture from '$lib/assets/profile.png';
   
    export let firstName = 'first name';
    export let lastName = 'last name';
    export let role = 'role';
    export let email = 'mail@mail.com';
    export let phone = 'phone';
    export let github = 'https://github.com';
    export let address = 'addr';
</script>

<header>
    <div>
        <h1>{firstName} {lastName}</h1>
        <h2>{role}</h2>
        <p><a href="mailto:{email}">{email}</a></p>
        <p><a href="phone:{phone}">{phone}</a></p>
        <p class="github"><a href="{github}" target="_blank">github</a></p>
        <p class="github for-print"><a href="{github}" target="_blank">{github}</a></p>
        <p>{address}</p>
    </div>
    <img src={profilePicture} alt="profil de Mattia Torsello" />
</header>

<style lang="scss">
    header {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding-bottom: 1rem;
        margin: 0 3rem;
        border-bottom: 2px solid #333;
        @media print {
            margin: 0 1rem;
            padding-bottom: 0.5rem;
        }
    }
    img {
        height: 100px;
    }

    .for-print {
        display: none;
    }
    @media print {
        .github {
            display: none;
        }
        .for-print {
            display: block;
        }
    }
</style>