<script>
	import { T } from '@threlte/core'
	import { Billboard, useTexture, interactivity, useCursor  } from '@threlte/extras'

    interactivity()

    let body = document.body

    const { hovering, onPointerEnter, onPointerLeave } = useCursor()

	const map1 = useTexture('./images/cage-2.png')
    const map2 = useTexture('./images/cage-3.png')

	let rad = Math.PI/180

	export let zoom = 0, id

    let scale = 2
    let size1 = [5.23/scale, 5.38/scale]
    let size2 = [5.56/scale, 5.78/scale]

	function handleClick(e) {
		id = e.object.userData.id
		console.log(id)
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
	rotation.x={-90*rad}/> -->

<!-- position ={[x,y,z]} -->
<!-- x = left-right -->
<!-- y = up-down -->
<!-- z = depth -->
<Billboard>
    {#await map1 then value}
  <T.Mesh 
		position={[3, 1, 0]}
		userData={{ id: 1 }}
		on:click={handleClick}
        on:pointerenter={onPointerEnter}
        on:pointerleave={onPointerLeave}
		>
    <T.MeshBasicMaterial map={value} transparent={true} />
    <T.PlaneGeometry args={size1} />
  </T.Mesh>

  <T.Mesh 
		position={[-2, 4, -40]}
		userData={{ id: 6 }}
		on:click={handleClick}
        on:pointerenter={onPointerEnter}
        on:pointerleave={onPointerLeave}
		>
    <T.MeshBasicMaterial map={value} transparent={true} />
    <T.PlaneGeometry args={size1} />
  </T.Mesh>

  <T.Mesh 
    position={[-1, 5, -20]}
    userData={{ id: 3 }}
    on:click={handleClick}
    on:pointerenter={onPointerEnter}
    on:pointerleave={onPointerLeave}
    >
    <T.MeshBasicMaterial map={value} transparent={true} />
    <T.PlaneGeometry args={size1} />
    </T.Mesh>   

    <T.Mesh 
        position={[2, 1, -30]}
        userData={{ id: 4 }}
        on:click={handleClick}
        on:pointerenter={onPointerEnter}
        on:pointerleave={onPointerLeave}
        >
        <T.MeshBasicMaterial map={value} transparent={true} />
        <T.PlaneGeometry args={size1} />
    </T.Mesh>
  {/await}
  {#await map2 then value}
  
  

    <T.Mesh 
        position={[-4, 3, -10]}
        userData={{ id: 2 }}
        on:click={handleClick}
        on:pointerenter={onPointerEnter}
        on:pointerleave={onPointerLeave}
        >
    <T.MeshBasicMaterial map={value} transparent={true} />
    <T.PlaneGeometry args={size2} />
    </T.Mesh>

  <T.Mesh 
		position={[-4, 2, -50]}
		userData={{ id: 5 }}
		on:click={handleClick}
        on:pointerenter={onPointerEnter}
        on:pointerleave={onPointerLeave}
        >
    <T.MeshBasicMaterial map={value} transparent={true} />
    <T.PlaneGeometry args={size2} />
  </T.Mesh>
	
  
  {/await}
</Billboard>

<!-- Ground -->
<!-- <T.Mesh rotation.x={90*rad}>
	<T.PlaneGeometry args={[100,100]}/>
	<T.MeshBasicMaterial color="grey" side={2}/>
</T.Mesh> -->