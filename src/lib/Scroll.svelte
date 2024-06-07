<div class="scroll">
    <p class="scroll-text">Scroll</p>
    <div class="arrow-container">
    <div class="arrow">
        <p>↓</p>
        <p>↓</p>
    </div>
    </div>
</div>

<style>
    .scroll {
		position: absolute;
		bottom: 10rem;
		width:100%;
		color:#f5f5f5;
		padding-top:2rem;
	}
	.scroll-text {
		width:100%;
		text-align: center;
		font-family: sans-serif;
		margin-bottom:0;
		font-size:0.8rem;
		font-family: 'Roboto Mono', monospace;
	}
	.arrow-container {
		margin-top:0;
		font-size:2rem;
		position:relative;
		overflow:hidden;
		height:2.5rem;
	}
	.arrow {
		font-size:2rem;
		position:absolute;
		left:50%;
		transform:translate(-50%,0);
		animation:down 2s infinite;
		animation-timing-function:ease-in-out;
	}
    .arrow > p {
        font-size: 1.24rem;
    }

	@keyframes down {
		from {bottom: 0rem}
		to {bottom:-2.6rem}
		}
</style>