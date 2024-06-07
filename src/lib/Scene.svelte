<script>
	import { T } from '@threlte/core'
	import { Billboard, useTexture, interactivity, useCursor  } from '@threlte/extras'
  import Cage from './Cage.svelte';

  export let open = false

    interactivity()

    let body = document.body

    const { hovering, onPointerEnter, onPointerLeave } = useCursor()

	const map1 = useTexture('./images/cage-1-ashy-tailorbird.png')
  const map2 = useTexture('./images/cage-2-yellow-vented-bulbul.png')
  const map3 = useTexture('./images/cage-3-common-green-magpie.png')
  const map4 = useTexture('./images/cage-4-green-leafbird.png')
  const map5 = useTexture('./images/cage-5-straw-headed-bulbul.png')
  const map6 = useTexture('./images/cage-6-bali-myna.png')
  const map7 = useTexture('./images/cage-7-javan-pied-starling.png')
  

	let rad = Math.PI/180

	export let zoom = 0, id

  let scale = 2
  function scaleSize(w, h) {
    return [
      w/scale, h/scale
    ]
  }

	function handleClick(e) {
		id = e.object.userData.id
		console.log(id)
    open = true
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

<Cage />

<!-- Light -->
<T.RectAreaLight 
	width="30" 
	height="30" 
	color="white" 
	intensity="2"
	position.y={4}
	rotation.x={-90*rad}/> -->



<!-- position ={[x,y,z]} -->
<!-- x = left-right -->
<!-- y = up-down -->
<!-- z = depth -->
<Billboard>
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

</Billboard>

<!-- Ground -->
<!-- <T.Mesh rotation.x={90*rad}>
	<T.PlaneGeometry args={[100,100]}/>
	<T.MeshBasicMaterial color="grey" side={2}/>
</T.Mesh> -->