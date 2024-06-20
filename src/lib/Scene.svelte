<script>
	import { T } from '@threlte/core'
	import { Billboard, useTexture, interactivity, useCursor  } from '@threlte/extras'
  import Cage from './Cage.svelte';

  export let open = false, select

  interactivity()

  let body = document.body

  const { hovering, onPointerEnter, onPointerLeave } = useCursor()

	// const map1 = useTexture('./images/cage-1-ashy-tailorbird.png')
  // const map2 = useTexture('./images/cage-2-yellow-vented-bulbul.png')
  // const map3 = useTexture('./images/cage-3-common-green-magpie.png')
  // const map4 = useTexture('./images/cage-4-green-leafbird.png')
  // const map5 = useTexture('./images/cage-5-straw-headed-bulbul.png')
  // const map6 = useTexture('./images/cage-6-bali-myna.png')
  // const map7 = useTexture('./images/cage-7-javan-pied-starling.png')
  

	let rad = Math.PI/180

	export let zoom = 0, id

  let scale = 2
  function scaleSize(w, h) {
    return [
      w/scale, h/scale
    ]
  }
</script>

<!-- Camera -->
<T.PerspectiveCamera
  makeDefault
  position={[0, 1, (10 - zoom)]}
  on:create={({ ref }) => {
    ref.lookAt(0, 1, 0)
  }}
/>

<!-- Light -->
<T.RectAreaLight 
	width="30" 
	height="30" 
	color="white" 
	intensity="2"
	position.y={4}
	rotation.x={-90*rad}
  position.z={-zoom}
  />

<Cage 
  image="ashy-tailorbird"
  imgW={6.82}  imgH={4.33}
  color="grey"
  x={-0.8}  y={1.5}  z={0}
  width={3} height={4} depth={2}
  rdeg={15}
  scale={5}
  footbar={2.3}
  id=1 bind:open bind:select {zoom}
/>

<Cage 
  image="yellow-vented-bulbul"
  imgW={5.08}  imgH={5.62}
  color="grey"
  x={1}  y={1}  z={-7}
  width={3} height={4} depth={2}
  rdeg={-10}
  scale={5}
  footbar={2.3}
  id=2 bind:open bind:select {zoom}
/>

<Cage 
  image="common-green-magpie"
  imgW={19.2}  imgH={10.8}
  color="grey"
  x={1.5}  y={1}  z={-14}
  width={3} height={4} depth={2}
  rdeg={5}
  scale={5}
  footbar={2.3}
  id=3 bind:open bind:select {zoom}
/>

<Cage 
  image="greater-green-leafbird"
  imgW={2.54}  imgH={7.58}
  color="grey"
  x={0.2}  y={2}  z={-21}
  width={3} height={4} depth={2}
  rdeg={0}
  scale={5}
  footbar={2.3}
  id=4 bind:open bind:select {zoom}
/>

<Cage 
  image="straw-headed-bulbul"
  imgW={5.82}  imgH={4.47}
  color="grey"
  x={-0.5}  y={1}  z={-28}
  width={3} height={4} depth={2}
  rdeg={-5}
  scale={5}
  footbar={2.3}
  id=5 bind:open bind:select {zoom}
/>

<Cage 
  image="bali-myna"
  imgW={5.39}  imgH={7.09}
  color="grey"
  x={0.5}  y={1}  z={-35}
  width={3} height={4} depth={2}
  rdeg={5}
  scale={5}
  footbar={2.3}
  id=6 bind:open bind:select {zoom}
/>

<Cage 
  image="javan-pied-starling"
  imgW={19.2}  imgH={10.8}
  color="grey"
  x={-2}  y={1}  z={-42}
  width={3} height={4} depth={2}
  rdeg={-10}
  scale={5}
  footbar={2.3}
  id=7 bind:open bind:select {zoom}
/>




<!-- <Billboard>
    {#await map1 then value}
      <T.Mesh 
        position={[-2, 1, 0]}
        userData={{ id: 1 }}
        on:click={handleClick}
            on:pointerenter={onPointerEnter}
            on:pointerleave={onPointerLeave}
        >
        <T.MeshBasicMaterial map={value} transparent={true} />
        <T.PlaneGeometry args={scaleSize(6.53, 5.68)} />
      </T.Mesh>
    {/await}
    {#await map2 then value}
      <T.Mesh 
        position={[3, -1, -7]}
        userData={{ id: 2 }}
        on:click={handleClick}
            on:pointerenter={onPointerEnter}
            on:pointerleave={onPointerLeave}
        >
        <T.MeshBasicMaterial map={value} transparent={true} />
        <T.PlaneGeometry args={scaleSize(5.24, 5.40)} />
      </T.Mesh>
    {/await}
    {#await map3 then value}
      <T.Mesh 
        position={[1.5, 1, -14]}
        userData={{ id: 3 }}
        on:click={handleClick}
            on:pointerenter={onPointerEnter}
            on:pointerleave={onPointerLeave}
        >
        <T.MeshBasicMaterial map={value} transparent={true} />
        <T.PlaneGeometry args={scaleSize(5.56, 5.79)} />
      </T.Mesh>
    {/await}
    {#await map4 then value}
      <T.Mesh 
        position={[-2, 0, -21]}
        userData={{ id: 4 }}
        on:click={handleClick}
            on:pointerenter={onPointerEnter}
            on:pointerleave={onPointerLeave}
        >
        <T.MeshBasicMaterial map={value} transparent={true} />
        <T.PlaneGeometry args={scaleSize(4.68, 4.43)} />
      </T.Mesh>
    {/await}
    {#await map5 then value}
      <T.Mesh 
        position={[-1, 1, -28]}
        userData={{ id: 5 }}
        on:click={handleClick}
            on:pointerenter={onPointerEnter}
            on:pointerleave={onPointerLeave}
        >
        <T.MeshBasicMaterial map={value} transparent={true} oapcity={0}/>
        <T.PlaneGeometry args={scaleSize(4.91, 5.94)} />
      </T.Mesh>
    {/await}
    {#await map6 then value}
      <T.Mesh 
        position={[0.5, 1, -35]}
        userData={{ id: 6 }}
        on:click={handleClick}
            on:pointerenter={onPointerEnter}
            on:pointerleave={onPointerLeave}
        >
        <T.MeshBasicMaterial map={value} transparent={true} />
        <T.PlaneGeometry args={scaleSize(4.47, 4.64)} />
      </T.Mesh>
    {/await}
    {#await map7 then value}
      <T.Mesh 
        position={[-2, 1, -42]}
        userData={{ id: 7 }}
        on:click={handleClick}
            on:pointerenter={onPointerEnter}
            on:pointerleave={onPointerLeave}
        >
        <T.MeshBasicMaterial map={value} transparent={true} />
        <T.PlaneGeometry args={scaleSize(5.53, 4.52)} />
      </T.Mesh>
    {/await}

</Billboard> -->

<!-- Ground -->
<!-- <T.Mesh rotation.x={90*rad}>
	<T.PlaneGeometry args={[100,100]}/>
	<T.MeshBasicMaterial color="grey" side={2}/>
</T.Mesh> -->