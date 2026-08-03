<script lang="ts">
	import * as Typeset from "$lib/registry/ui/typeset/index.js";
</script>

<Typeset.Root class="w-full max-w-2xl">
	<h1>Typeset preview</h1>
	<p>
		Typeset provides a consistent reading surface for rendered content. It is designed for chat
		responses, documentation, and other long-form UI where spacing should remain stable as content
		arrives.
	</p>
	<h2>Readable defaults</h2>
	<p>
		Use <strong>emphasis</strong>, <em>italics</em>, and <code>inline code</code> without adding a separate
		class to every element.
	</p>
	<blockquote>
		Good typography makes content easier to scan before it makes it look beautiful.
	</blockquote>
	<h3>What it covers</h3>
	<ul>
		<li>Headings and paragraphs with predictable rhythm.</li>
		<li>Lists, links, blockquotes, and inline formatting.</li>
		<li>Code blocks and tables that remain usable at smaller widths.</li>
	</ul>
	<pre><code>const answer = await getResponse(&#123; prompt &#125;);</code></pre>
	<table>
		<thead>
			<tr><th>Layer</th><th>Responsibility</th></tr>
		</thead>
		<tbody>
			<tr><td>Shell</td><td>Owns the surrounding layout.</td></tr>
			<tr><td>Typeset</td><td>Owns content rhythm and readable defaults.</td></tr>
		</tbody>
	</table>
</Typeset.Root>
