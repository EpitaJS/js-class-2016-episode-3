# Change logs for Labella.js

## v1.x.x

<a name="1.0.0"></a>
### 1.0.0 (2016-01-23)

Replace *force-directed simulation* with *constraint-based layout* and use [VPSC](https://github.com/tgdwyer/WebCola/wiki/What-is-VPSC%3F) quadratic solver to compute positions that best satisfy the constraints. This method is much faster and does not rely on number of iterations like a simulation, therefore the computation can return results immediately and does not need to be asynchronous anymore. This improves overall performance and leads to several changes to the API.

<a name="migrate-0.x.x-1.x.x"></a>
#### New API

- `force.compute()` is a replacement for `force.start()` and `force.on()`. Usage is slightly different because `force.compute()` is synchronous and the nodes' positions are ready immediately after the call while `force.start()` was asynchronous.

```diff
var force = new labella.Force()
  .nodes(nodes)
-   .on('end', function(){
-     draw(force.nodes());
-   })
-   .start(100);
+   .compute();
+ draw(force.nodes());
```

- New **Force** option `lineSpacing` is available for setting the minimum gap between lines.

#### Breaking changes

- The following **Force** functions are deprecated: `.on()`, `.start()`, `.stop()`, `.resume()`, `.step()` and `.isStable()`.
- The following **Force** options are deprecated: `damping`, `epsilon` and `roundsPerTick`
- `node.getLevel()` is renamed to `node.getLayerIndex()`

## v0.x.x

<a name="0.1.1"></a>
### 0.1.1 (2015-11-21)

#### Breaking changes

- For the **Force**, use ```options.minPos``` and ```options.maxPos``` to set ```options.layerWidth``` for the **Distributor** inside it instead of having to specify ```options.layerWidth``` explicitly.
- Change ```options.labelHeight``` in **Renderer** to ```options.nodeHeight```.

<a name="0.1.0"></a>
### 0.1.0 (2015-11-20)

First release. Hello, World!