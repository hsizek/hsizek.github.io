+++
date = '2026-04-25T10:16:49-04:00'
draft = false
title = 'Cyclic Crop Rotations'
keywords = ['agicuture', 'crop', 'crop rotation']

+++
One of the difficulties of doing crop rotation analysis is that you're given a crop sequence that you need to interpret as a crop rotation. Perhaps the crop rotation changes through time and perhaps even changes the length of the crop rotation. People use a plethora of different methods to analyze crop sequences which I add my tool to. 
<!--more-->

Crop rotations can be superimposed upon crop sequences to determine a potential realization of what crop rotation is used through time. 

## Defining crop rotations
Crop rotations can be framed as a mathematical object. We could have an empty rotation $\langle \rangle$ or one with a crop in it $\langle 0 \rangle$ or multiple crops in it $\langle 0,1,1 \rangle$. We can define the an additive operation $\langle 0 \rangle+\langle 1 \rangle=\langle 0,1 \rangle$. They are idemnopotent. The rotation $\langle 1,1 \rangle$ is the same as $\langle 1 \rangle$. But they are not associative, $\langle 0,1,1 \rangle = \langle 0 \rangle + \langle 1 \rangle + \langle 1 \rangle \neq \langle 0 \rangle + (\langle 1 \rangle + \langle 1 \rangle) = \langle 0,1 \rangle$ is not the same as $\langle 0,1 \rangle$, nor commutative $\langle 0 \rangle + \langle 1 \rangle + \langle 2 \rangle \neq \langle 0 \rangle + \langle 2 \rangle + \langle 1 \rangle$. But they can be bijected, $\sigma(\langle 0,1 \rangle) = \langle 1,0 \rangle$. Multiplication is not really a valid operator, nor is division, inverses aren't well defined. 

This is all fine and dandy, but it doesn't relate to crop sequences that easily. We could instantiate repetitions of multiple crop rotations concated together to form crop sequences. But how do you go from crop sequences (i.e. what is observed) to crop rotations. 

Ideally, the process to go from crop sequence to crop rotations should be deterministic, so that the results are consistent between different crop sequences and there aren't biases based on crop composition. There are two ways of doing this. 

### Set coverage
It could be thought of as a set cover problem, where the covering sets are blocks of consistent rotations in a sequence. In this formulation, it becomes important to consider what is considered to be block, if a rotation has to fully complete or if it can partially repeat less than two times, e.g. is 00100 a repetition of a three year rotation? 

### Compression algorithms
Crop rotations can be viewed as a way to compress crop sequence information through time. 01011010 could be compressed into $(01)^2+(10)^2$ or $0+(101)^2+0$. Which pattern is chosen is based on the specifics of the compression algorithm and the cost function parameters.  
I found that a compression algorithm with a cost of $c*\sqrt{2-e^{-k_l(|r|-1)}} * \sqrt{2-e^{-k_r(|r_{rep}|-1)}}$ works ok, with an initial cost of 1 per token. The two components are confined so that rotations are always cheaper than stand alone. 