<script>
    import { T } from '@threlte/core'
    import { Billboard, useTexture, useCursor } from '@threlte/extras'

    const { hovering, onPointerEnter, onPointerLeave } = useCursor()

    export const image = ""

    export const color = "grey"
    export let x = 2, y = 1, z = 0
    export let width = 3, height = 4, depth = 2
    export let rdeg = 0
    export let url = 'bird-sample-01'

    export let open = false, id

    let rad = Math.PI/180

    let thick = 0.02
    let ribcount = 8

    let ribsX = width/(ribcount)
    let ribsZ = depth/(ribcount)
    let map = useTexture(`./images/${url}.png`)

    let scale = 3

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

<T.Object3D
    position.x={x}
    position.y={y}
	position.z={z}
    rotation.y={rad*rdeg}
>
    <Billboard>
        {#await map then value}
        <T.Mesh 
            position={[x, y-height/2, z]}
            rotation.y={rad*rdeg}
            userData={{ id: 1 }}
            on:click={handleClick}
            on:pointerenter={onPointerEnter}
            on:pointerleave={onPointerLeave}
            >
            <T.MeshBasicMaterial map={value} transparent={true} />
            <T.PlaneGeometry args={scaleSize(6, 6)} />
        </T.Mesh>
        {/await}
    </Billboard>

    <!-- FRONT RIBS -->
    {#each Array(ribcount+1) as _,i}
        <T.Mesh
            position.x={x-(i*ribsX)+(width/2)}
            position.y={y-height/2}  
            position.z={z+depth/2}>
            <T.BoxGeometry args={[thick,height,thick]}/>
            <T.MeshStandardMaterial color={color} side={2}/>
        </T.Mesh>
    {/each}

    <!-- BACK RIBS -->
    {#each Array(ribcount+1) as _,i}
        <T.Mesh
            position.x={x-i*ribsX+width/2}
            position.y={y-height/2}  
            position.z={z-depth/2}>
            <T.BoxGeometry args={[thick,height,thick]}/>
            <T.MeshStandardMaterial color={color} side={2}/>
        </T.Mesh>
    {/each}

    <!-- LEFT RIBS -->
    {#each Array(ribcount+1) as _,i}
        <T.Mesh
            position.z={z+i*ribsZ-depth/2}
            position.y={y-height/2}  
            position.x={x-width/2}>
            <T.BoxGeometry args={[thick,height,thick]}/>
            <T.MeshStandardMaterial color={color} side={2}/>
        </T.Mesh>
    {/each}

    <!-- RIGHT RIBS -->
    {#each Array(ribcount+1) as _,i}
        <T.Mesh
            position.z={z+i*ribsZ-depth/2}
            position.y={y-height/2}  
            position.x={x+width/2}>
            <T.BoxGeometry args={[thick,height,thick]}/>
            <T.MeshStandardMaterial color={color} side={2}/>
        </T.Mesh>
    {/each}

    <!-- TOP RIBS -->
    {#each Array(ribcount+1) as _,i}
        <T.Mesh
            position.x={x-i*ribsX+width/2}
            position.y={y}
            position.z={z}>
            <T.BoxGeometry args={[thick,thick,depth]}/>
            <T.MeshStandardMaterial color={color} side={2}/>
        </T.Mesh>
    {/each}

    <!-- BOTTOM RIBS -->
    {#each Array(ribcount+1) as _,i}
        <T.Mesh
            position.x={x-i*ribsX+width/2}
            position.y={y-height}
            position.z={z}>
            <T.BoxGeometry args={[thick,thick,depth]}/>
            <T.MeshStandardMaterial color={color} side={2}/>
        </T.Mesh>
    {/each}

    <!-- TOP RING -->
    <T.Mesh
        position.z={z-depth/2}
        position.y={y}
        position.x={x}>
		<T.BoxGeometry args={[width+thick*2,thick*4,thick*2]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <T.Mesh
        position.z={z+depth/2}
        position.y={y}
        position.x={x}>
		<T.BoxGeometry args={[width+thick*2,thick*4,thick*2]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <T.Mesh
        position.z={z}
        position.y={y}
        position.x={x+width/2}>
		<T.BoxGeometry args={[thick*2,thick*4,depth+thick*2]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <T.Mesh
        position.z={z}
        position.y={y}
        position.x={x-width/2}>
		<T.BoxGeometry args={[thick*2,thick*4,depth+thick*2]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <!-- BOTTOM RING -->
    <T.Mesh
        position.z={z-depth/2}
        position.y={y-height}
        position.x={x}>
		<T.BoxGeometry args={[width+thick*2,thick*4,thick*2]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <T.Mesh
        position.z={z+depth/2}
        position.y={y-height}
        position.x={x}>
		<T.BoxGeometry args={[width+thick*2,thick*4,thick*2]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <T.Mesh
        position.z={z}
        position.y={y-height}
        position.x={x+width/2}>
		<T.BoxGeometry args={[thick*2,thick*4,depth+thick*2]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <T.Mesh
        position.z={z}
        position.y={y-height}
        position.x={x-width/2}>
		<T.BoxGeometry args={[thick*2,thick*4,depth+thick*2]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <!-- BAR FOOT -->
    <T.Mesh
        position.z={z}
        position.y={y-height/3*2}
        position.x={x}>
		<T.BoxGeometry args={[width+thick*2,thick*2,thick*2]}/>
		<T.MeshStandardMaterial color="white" side={2}/>
	</T.Mesh>

    

</T.Object3D>