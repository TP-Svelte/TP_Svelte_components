<script>
    import UserCard from "./components/UI/UserCard.svelte";

    let persons = [{
        name: 'Maxime',
        cover: 'https://images.unsplash.com/photo-1657664065994-5e257c88b7f8?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1683&q=800'
    },
        {name: 'Jul',
        cover: 'https://images.unsplash.com/photo-1662425877955-1092c2e1309e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1771&q=80'
    },
        {name: 'Jul',
        cover: 'https://images.unsplash.com/photo-1657664065994-5e257c88b7f8?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1683&q=80'
    },
    ]
</script>

<UserCard persons={persons} />