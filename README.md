# 3x3-last-layer-simple-simple
The fewest algs required for a 3x3 last layer, AFAIK

# Move Notation

I'm using standard singmaster notation. Faces are labeled

- U (up) -- top face
- D (down) -- bottom face
- L (left) -- left face
- R (right) -- right face
- F (front) -- front face
- B (back) -- back face

note: the most common confusion is to read B as "bottom"... avoid this mistake.

We use a face name to represent a clockwise motion, and a "prime"d name for a counterclockwise motion, and a 2 to indicate a half-turn (two quarter-turns). So, for instance UF'D2 would indicate a clockwise turn of the upper face, a counterclockwise motion of the front face, and a double-turn of the down face.

# Mathy overview

A 3x3 puzzle is essentially an exercise in physical group theory. A puzzle consists of corner pieces and edge pieces. The corners can be permuted and independently oriented (subject to some parity constraints; you can't just rotate one corner through a set of legal moves), and the edges can be permuted and independently oriented.

Most solution plans essentially consists of an ordering on permutation & orientation "fixes" in a predetermined order. One standard plan is to do orientation and permutation simultaneously to bring a full layer into correctness, then do the same for the edges that make up the second layer, then tackle the last layer. 

I'm only going to talk about the last layer.

# Last Layer Plan

Here's the simple plan:

1) orient the four remaining edge pieces,
2) permute the four remaining edge pieces,
3) permute the four remaining corner pieces, and
4) orient the four remaining corner pieces.

Each of these can be accomplished with a single algorinthm (sequence). I'd like to emphasize here that my only metric here is "least memorization". I don't care at all about speed, I'm just showing what I believe to be the method that requires the least memorization.

Also, as you'll see, my approach is going to lean very heavily on your own ability to observe & discover.

Finally, be sure in the following that the last layer is on the Up face, or none of this will make any sense at all.

## Edge Orientation

Here's the algorithm:

```
FRUR'U'F'
```
Notice that this is basically just the conjugate of a [R/U sexy move](https://www.speedsolving.com/wiki/index.php/Sexy_Move); specifically, it's placed within an F/F' pair.

Use this algorithm interleaved with Up face rotations to orient the four edges. How? Well, you'll figure it out. 

Specifically, observe the action of this move on the permutation & orientation of the four Up edges, and figure out how to rotate the Up face in order to make this algorithm do what you want. I could tell you, but it's more fun to figure it out yourself.

## Edge Permutation

Here's the algorithm:

```
RUR'URU2R'
```

This one has a very up down up down feel to me, with the pieces of a full Up rotation interleaved. Again, figure out the action of this move on the edge pieces, and how to use it to permute them correctly. Since this move doesn't affect the orientation of the edges, it's easier to mentally track the action of this move.

## Corner Permutation

Here's the algorithm:

```
R'ULU'RUL'U'
```

If you watch the up/back corners on this one, you'll see that there one of them that just keeps dodging back and forth, and completely avoids the meat grinder of the L/L' and R'/R wheels. That just makes it easier to memorize. 

Again, figure out how it works and use it to *permute* the corners. Don't worry about their orientation yet.

## Corner Orientation

This one's a bit weird, until you get the hang of it. Consider this sexy move:

```
R'D'RD
```

(or, honestly, *any* sexy move pair including a side face and the down face). Do it 6 times. Hey, we're back where we started! In group theoretic terms, the sexy move has an order of 6. Here's the interesting thing. Do it 2 times, and look at the URF corner. It's in the same location as it was at the beginning, but it's oriented differently. Now do it another 2 times. Same thing. Now do it another 2 times. You're back where you started. So, here's the tricky bit. Since you have different corners that need to be oriented, what you do is to do 2x or 4x the sexy move, then do an Up face rotation, then finish the last 2x or 4x of the sexy move to repair the lower two layers.

Done!
