# third
Thinking of how to express three js as vnode.

```js
import React, {
  useState
} from 'react'
import { 
  useScene,
  usePerspectiveCamera,
  useOrthographicCamera,
  ThirdView
} from 'react-third'

function PresudoThirdView (){
  const [ rotateXY, setRotateXY ] = useState()

  const thirdScene = useScene((x)=>(
    <x.scene>
      <x.group position={[0,0,0]} rotation={[...rotateXY,0]}>
        <x.mesh onClick="handleClickMesh">
          <x.boxBufferGeometry args={[1, 1, 1]} />
          <x.meshStandardMaterial color={'orange'} />
        </x.mesh>
        <x.css2DObject>
          <a onClick="handleClickButton">Hello</a>
        </x.css2DObject>
      </x.group>
      <x.pointLight position={[10, 10, 10]} />
    </x.scene>
  ))

  const camera1 = usePerspectiveCamera({fov: 75, near: 0.1, far: 1000, z: 5, lookAt: [0,0,0]})
  const camera2 = useOrthographicCamera({near: 0.1, far: 1000, z: 5, lookAt: [0,0,0]})

  thirdScene.useFrame((time)=>{
    const rotation = 1 * time/10000
    setRotateXY([rotation, rotation])
  })


  function handleClickMesh (){
    alert('click mesh!')
  }

  function handleClickButton(){
    alert('hello world!')
  }

  return (
    <div>
      <h1>Third example page</h1>
      <ThirdView scene={thirdScene} camera={camera1} style={width:100, height:100} />
      <ThirdView scene={thirdScene} camera={camera2} style={width:100, height:100} />
    </div>
  )
}
```

I would like to implement it if possible
