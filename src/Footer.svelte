<script>
    async function getVersion() {
        const res = await fetch("http://localhost:8080/api/version");
        if (!res.ok) {
            throw new Error(await res.text());
        }
        return res.json();
    }
</script>

<div id="footer">
    <div class="left">
        <p>
            &copy; 2020 Michael D Henderson
            |
            {#await getVersion()}
                <a href="https://github.com/mdhender/server">Gas Giant Battles</a>
            {:then versionResponse}
                <a href="https://github.com/mdhender/server">Gas Giant Battles {versionResponse.data.semver}</a>
            {:catch error}
                <div class="error">Error: {error.message}</div>
            {/await}
            | Template design by <a href="https://github.com/mdhender/server/VIKLUND.md">Andreas Viklund</a>
        </p>
    </div>
    <div class="right textright">
        <p>Sample footer menu: <a href="#">Link 1</a> | <a href="#">Link 2</a> | <a href="#">Link 3</a></p>
        <p class="hide"><a href="#top">Return to top</a></p>
    </div>
</div>
