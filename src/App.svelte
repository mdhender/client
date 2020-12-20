<script>
	import {site} from './stores/site';
	import Footer from './Footer.svelte';
</script>

<div id="top">
	<p id="skiplinks">Skip to: <a href="#content">content</a> | <a href="#sidebar">sidebar</a></p>
	<div id="sitetitle">
		<h1><a href="/">{$site.site.title}</a></h1>
		<p>{$site.site.slug}</p>
	</div>
	<hr class="clear"/>
</div>

<div id="wrap">
	<div id="mainmenu">
		{#each $site.mainMenu as menu}
			<dl class="{menu.class}">
				<dt><a href="{menu.link}">{menu.label}</a></dt>
				{#each menu.children as link}
					{#if link.link}
						<dd><a href="{link.link}">{link.label}</a></dd>
					{:else}
						<dd>{link.label}</dd>
					{/if}
				{/each}
			</dl>
		{/each}
		<hr class="clear"/>
	</div>

	<div id="content">
		{#if $site.content}
			<h2><a href="#">{$site.content.title}</a></h2>
			{#each $site.content.paragraphs as p, i}
				{#if i === 0}
					<p class="introtext">{p}</p>
				{:else}
					<p>{p}</p>
				{/if}
			{/each}

			<div class="trio1">
				<h3><a href="#">Support the development</a></h3>
				<p>If you want to support the development of this game, there are plenty of opportunities.</p>
				<ul>
					<li>Coding</li>
					<li>Testing</li>
					<li>Documenting</li>
					<li>Spreading the word</li>
				</ul>
				<p>Read more...</p>
			</div>

			<div class="trio2">
				<h3><a href="#">How to join</a></h3>
				<p>
					Libero volutpat sed cras ornare arcu dui.
					Accumsan lacus vel facilisis volutpat.
				</p>
				<p>
					Sit amet risus nullam eget felis eget nunc.
					Scelerisque eleifend donec pretium vulputate sapien nec.
					Placerat duis ultricies lacus sed turpis tincidunt id aliquet.
				</p>
				<p>
					In ornare quam viverra orci sagittis eu volutpat.
					Pellentesque habitant morbi tristique senectus et netus et.
				</p>
				<p>Read more...</p>
			</div>

			<div class="trio3">
				<h3><a href="#">Customization</a></h3>
				<p>
					Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
					tempor incididunt ut labore et dolore magna aliqua.
					Egestas sed sed risus pretium quam.
					Ut aliquam purus sit amet luctus.
				</p>
				<p>
					Pellentesque habitant morbi tristique senectus et netus et malesuada.
					Integer quis auctor elit sed vulputate mi sit amet.
					Duis ultricies lacus sed turpis tincidunt id aliquet risus.
					Ut morbi tincidunt augue interdum velit euismod in pellentesque massa.
					A cras semper auctor neque vitae tempus quam.
				</p>
				<p>Read more...</p>
			</div>
		{/if}
		<hr class="clear"/>
	</div>

	<div id="sidebar">
		<h2>Eleifend pretium</h2>
		<p>
			Tellus id interdum velit laoreet id. Commodo quis tincidunt nunc pulvinar sapien et ligula.
		</p>

		<div class="left">
			<h2>Games</h2>
			<ul class="sidemenu">
				{#each $site.menu.left as menu}
					<li>
						<a href="{menu.link}">{menu.label}</a>
						{#if menu.children}
							<ul>
								{#each menu.children as child}
									<li><a href="{child.link}">{child.label}</a></li>
								{/each}
							</ul>
						{/if}
					</li>
				{/each}
			</ul>

			<h2>Documentation</h2>
			<ul>
				<li><a href="#">Rules</a></li>
				<li><a href="#">Submitting Orders</a></li>
				<li><a href="#">Tutorials</a></li>
				<li><a href="#">Known Issues</a></li>
			</ul>

			<h2>Sample links</h2>
			<ul>
				{#each $site.menu.sample as menu}
					<li><a href="{menu.link}">{menu.label}</a></li>
				{/each}
			</ul>
		</div>

		<div class="right">
			<h2>Game 100, Turn 13</h2>
			<ul class="sidemenu">
				{#each $site.menu.right as menu}
					<li>
						<a href="{menu.link}">{menu.label}</a>
						{#if menu.children}
							<ul>
								{#each menu.children as child}
									<li><a href="{child.link}">{child.label}</a></li>
								{/each}
							</ul>
						{/if}
					</li>
				{/each}
			</ul>

			{#if $site.notice}
				<h2>{$site.notice.title}</h2>
				<p>{@html $site.notice.text}</p>
			{/if}
		</div>
		<hr class="clear"/>
	</div>
	<hr class="clear"/>
</div>

<Footer />