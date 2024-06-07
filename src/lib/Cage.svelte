<script>
    import { T } from '@threlte/core'
    export let width, height, depth, image
    export let color = "grey"
</script>

<T.Object3D
    position.x=2
    position.y=1
	position.z=0
>
    {#each Array(20) as _,i}
    <T.Mesh
        position.x={i/10}
        position.z={0}>
		<T.BoxGeometry args={[0.01,2,0.01]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>
    {/each}

    {#each Array(20) as _,i}
    <T.Mesh 
        position.x={i/10}
        position.z={-2}>
		<T.BoxGeometry args={[0.01,2,0.01]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>
    {/each}

    {#each Array(20) as _,i}
    <T.Mesh
        position.z={i/-10}
        position.x={0}>
		<T.BoxGeometry args={[0.01,2,0.01]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>
    {/each}

    {#each Array(20) as _,i}
    <T.Mesh
        position.z={i/-10}
        position.x={2}>
		<T.BoxGeometry args={[0.01,2,0.01]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>
    {/each}

    <T.Mesh
        position.z={0}
        position.y={1}
        position.x={1}>
		<T.BoxGeometry args={[2,0.04,0.02]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <T.Mesh
        position.z={-2}
        position.y={1}
        position.x={1}>
		<T.BoxGeometry args={[2,0.04,0.02]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <T.Mesh
        position.z={0}
        position.y={-1}
        position.x={1}>
		<T.BoxGeometry args={[2,0.04,0.02]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <T.Mesh
        position.z={-2}
        position.y={-1}
        position.x={1}>
		<T.BoxGeometry args={[2,0.04,0.02]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <T.Mesh
        position.z={-1}
        position.y={-1}
        position.x={0}>
		<T.BoxGeometry args={[0.02,0.04,2]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <T.Mesh
        position.z={-1}
        position.y={-1}
        position.x={2}>
		<T.BoxGeometry args={[0.02,0.04,2]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <T.Mesh
        position.z={-1}
        position.y={1}
        position.x={0}>
		<T.BoxGeometry args={[0.02,0.04,2]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

    <T.Mesh
        position.z={-1}
        position.y={1}
        position.x={2}>
		<T.BoxGeometry args={[0.02,0.04,2]}/>
		<T.MeshStandardMaterial color={color} side={2}/>
	</T.Mesh>

</T.Object3D>