# Dunes

<p align="center">
  <img src="./renders/2.png" width="800px"/>
</p>

## About This Work

This was a technical exploration more than anything, a chance to experiment with
generating realistic sand using noise textures and displacement, combined with
adaptive subdivision to control geometry density. I also wanted to play around
with mixing glass and volume shaders to create those interesting transparent
objects you see scattered across the dunes.

I didn't use any reference images for this. The inspiration actually came from
those abstract, geometric math textbooks we all had in middle school, the ones
with the inexplicably cool covers that had nothing to do with algebra. There's
something appealing about that kind of abstract, technical aesthetic.

This was purely a personal technical exercise. I'll be honest: the artistic
value is lower for me on this one. It was more about figuring out how these
specific tools work in Blender than creating something meaningful.

## My Process

The sand was the main technical challenge. I layered different scales of Voronoi
<sup>[1]</sup> textures together, mixing in some noise to break up the
repetition that Voronoi can create. This gave me the granular, organic look I
was going for, but it came at a cost, the computation was expensive.

I used adaptive subdivision <sup>[2]</sup> on a flat plane to optimize where the
geometry was being subdivided. The idea was to only add detail where the
displacement needed it, which theoretically should have been efficient. And it
was, in terms of final polygon count, but the workflow itself was frustrating.

For the glass objects, I experimented with combining glass and volume shaders in
different ratios to get that semi-transparent, almost liquid look. This part was
more enjoyable because I could iterate faster.

## What I Liked

The adaptive subdivision did what it was supposed to do, it optimized the mesh
subdivisions effectively, only adding geometry where the displacement demanded
it. When it all finally rendered, the sand texture had a nice, natural quality
to it, and the layering of Voronoi and noise paid off visually.

The glass/volume shader experiments were fun and yielded some cool-looking
transparent objects. There's something satisfying about getting materials to
look "right" even when you're not quite sure what "right" means in an abstract
piece like this.

## Lessons Learned

The biggest lesson here: I don't really like working with adaptive subdivision
and texture displacement. The viewport doesn't give you an accurate
representation of what the final result will look like, so I spent a lot of time
flipping back and forth between the viewport and rendered view trying to figure
out what the hell was actually happening. It was frustrating.

I strongly prefer workflows where I get instant feedback. This wasn't that. The
expensive textures made the final adjustment stage especially cumbersome, every
tweak meant waiting for another render to see if it actually improved anything.

If I were to do this again, I'd look for more efficient options for creating
sand. Maybe a different texture setup, or a shader approach that doesn't require
as much displacement geometry. The end result looked okay, but the juice wasn't
really worth the squeeze in terms of iteration time.

I also learned that technical exercises are valuable, but they need to be
balanced with projects that have more artistic intent. This was good for
understanding these specific tools, but it didn't give me the same satisfaction
as creating something with a clearer vision or emotional direction.

Next time I want to experiment with displacement, I'll probably start simpler
and build up complexity gradually, rather than jumping straight into layered
Voronoi with adaptive subdivision. Small wins that let me iterate quickly are
better than big ambitious setups that lock me into long render times.

## References

1. [https://en.wikipedia.org/wiki/Worley_noise](https://en.wikipedia.org/wiki/Worley_noise)
2. [https://docs.blender.org/manual/en/4.0/render/cycles/object_settings/adaptive_subdiv.html](https://docs.blender.org/manual/en/4.0/render/cycles/object_settings/adaptive_subdiv.html)

[1]: https://en.wikipedia.org/wiki/Worley_noise
[2]: https://docs.blender.org/manual/en/4.0/render/cycles/object_settings/adaptive_subdiv.html
