
# Particle Animations Example

This small showcase implements various particle animations using mathematical equations. Each animation type is defined by a set of equations governing the movement of particles. Included are the mathematical expressions for each animation.
<br>

**Note:** The GIFs below illustrate the visual representation of particle animations--aliases for each are pseudorandom. The mathematical formulas are provided for each animation type, where:
- \( y' \): Updated value for the y-coordinate of a particle.
- \( x' \): Updated value for the x-coordinate of a particle.
- \( z' \): Updated value for the z-coordinate of a particle.
- \( t \): Time variable representing the animation's progression.
<br>
<details>
  <summary>How to Implement Particle Animations</summary>
  <br>
  <p><i>Note: Ensure you have a basic Three.js scene setup before proceeding.</i></p>
  <p>

  ```javascript
    import * as THREE from 'three'

    // Particle geometry
    const particlesGeo = new THREE.BufferGeometry()
    const count = 3000;

    const positions = new Float32Array(count * 3)
    const colors = new Float32Array(count * 3)

    const colorList = Object.values(THREE.Color.NAMES);

    for (let i = 0; i < count * 3; i++) {
      positions[i] = Math.random()
      colors[i] = Math.random()
    }

    particlesGeo.setAttribute('position', new THREE.BufferAttribute(positions, 3))
    particlesGeo.setAttribute('color', new THREE.BufferAttribute(colors, 3))

    // Particle material
    const particlesMaterial = new THREE.PointsMaterial({
      size: 0.03,
      sizeAttenuation: true,
      transparent: true,
      depthWrite: false,
      blending: THREE.AdditiveBlending,
      vertexColors: true,
    })

    // Particle system
    const particles = new THREE.Points(particlesGeo, particlesMaterial)
    scene.add(particles)

    //Animation Example
    const AnimationType = {
      DimensionSteal: function () {
        for(let i = 0; i < count; i++) {
                const i3 = i * 3;
                const x = particlesGeo.attributes.position.array[i3]
                const y = particlesGeo.attributes.position.array[i3 + 1]
                const z = particlesGeo.attributes.position.array[i3 + 2]

            particlesGeo.attributes.position.array[i3 + 1] = Math.sin(clock.getElapsedTime() + x) * 1.3
            particlesGeo.attributes.position.array[i3] = Math.cos(clock.getElapsedTime() + x * y * z) * 1.3
            particlesGeo.attributes.position.array[i3 + 2] = Math.cos(clock.getElapsedTime() + x - y / z) * 1.3
        }

        particlesGeo.attributes.position.needsUpdate = true

    }
}

// Animation loop
function runnable(){
    AnimationType.DimensionSteal()
    window.requestAnimationFrame(runnable)
}

// Start animation loop
runnable();

```
  </p>
</details>
<br>


1. **DimensionSteal:**
   - $y' = \sin(t + x) \cdot 1.3$
   - $x' = \cos(t + x \cdot y \cdot z) \cdot 1.3$
   - $z' = \cos(t + x - \frac{y}{z}) \cdot 1.3$
  
    ![animations/DimensionSteal.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/DimensionSteal.gif)

2. **BreakawaySplitCollapse:**
   - $y' = \sin(t + x) \cdot 1.3$
   - $z' = \cos(t + x) \cdot 1.3$
  
    ![animations/BreakawaySplitCollapse.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/BreakawaySplitCollapse.gif)

3. **WaveRecursion:**
   - $y' = \sin(t + x) \cdot 1.3$
   - $z' = \cos(t) \cdot 1.3$
  
    ![animations/WaveRecursion.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/WaveRecursion.gif)

4. **FloatingWave:**
   - $y' = \sin(t + x) \cdot 1.3$
   - $z' = \cos(t + x \cdot 2\pi) \cdot 1.3$
  
    ![animations/FloatingWave.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/FloatingWave.gif)

5. **VariantWave:**
   - $y' = \sin(t + x) \cdot 1.3$
   - $z' = \cos(t + x \cdot y) \cdot 1.3$
  
    ![animations/VariantWave.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/VariantWave.gif)

6. **VariantWaveCollapse:**
   - $y' = \sin(t + x) \cdot 1.3$
   - $z' = \cos(t + x / y) \cdot 1.3$
  
    ![animations/VariantWaveCollapse.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/VariantWaveCollapse.gif)

7. **DoubleEndedWave:**
   - $y' = \sin(t + x) \cdot 1.3$
   - $z' = \cos(t + x / y) \cdot 1.3 $
  
    ![animations/DoubleEndedWave.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/DoubleEndedWave.gif)

8. **FakeStomachAcid:**
   - $y' = \sin(t + x) \cdot 1.3$
   - $z' = \cos(t + x / y \cdot z) \cdot 1.3$
  
    ![animations/FakeStomachAcid.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/FakeStomachAcid.gif)

9. **FakeCollapseCircle:**
   - $y' = \sin(t + x) \cdot 1.3$
   - $z' = \cos(t + x \cdot y \cdot z) \cdot 1.3$
  
    ![animations/FakeCollapseCircle.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/FakeCollapseCircle.gif)

10. **AttackingWorm:**
    - $y' = \sin(t + x) \cdot 1.3$
    - $z' = \cos(t + x \cdot y \cdot z) \cdot 1.3$
   
     ![animations/AttackingWorm.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/AttackingWorm.gif)

11. **TailwhipFlip:**
    - $y' = \sin(t + x) \cdot 1.3$
    - $z' = \cos(t + x \cdot y \cdot z) \cdot 1.3$
   
     ![animations/TailWhipFlip.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/TailwhipFlip.gif)

12. **DimensionTeleportCollapse:**
    - $y' = \sin(t + x) \cdot 1.3$
    - $z' = \cos(t + x / y \cdot z) \cdot 1.3$
   
     ![animations/DimensionTeleportCollapse.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/DimensionTeleportCollapse.gif)

13. **Desynchronization:**
    - $y' = \sin(t + x) \cdot 1.3$
    - $z' = \cos(t + x / y / z) \cdot 1.3$
   
     ![animations/Desyncrhonization.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/Desyncrhonization.gif)

14. **Teleportation:**
    - $y' = \sin(t + x) \cdot 1.3$
    - $z' = \cos(t + x / y / z) \cdot 1.3$
   
     ![animations/Teleportation.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/Teleportation.gif)

15. **Slipspace:**
    - $y' = \sin(t + x) \cdot 1.3$
    - $z' = \cos(t + x \cdot y \cdot z) \cdot 1.3$
    - $y' = \cos(t + x / y / z) \cdot 1.3$
   
     ![animations/Slipspace.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/Slipspace.gif)

16. **Opposispace:**
    - $y' = \sin(t + x) \cdot 1.3$
    - $z' = \cos(t + x) \cdot 1.3$
    - $z' = \cos(t + x \cdot y \cdot z) \cdot 1.3$
   
     ![animations/Opposispace.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/Opposispace.gif)

17. **ZigZag:**
    - $x' = \sin(t \cdot x) \cdot 1.3$
    - $y' = \cos(t) \cdot 2$
    - $z' = \tan(t) \cdot 2$
   
     ![animations/ZigZag.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/ZigZag.gif)

18. **Sinevis:**
    - $x' = \cos(t) \cdot \sin(t \cdot x) \cdot \frac{1.3}{\pi}$
    - $y' = -\sin(t \cdot y) \cdot 1.3 - \frac{\cos(t)}{\pi}$
    - $z' = \cos(t \cdot z) \cdot 1.3$
   
     ![animations/Sinevis.gif](https://github.com/rewindbytes/ParticleAnimations/blob/main/animations/Sinevis.gif)
