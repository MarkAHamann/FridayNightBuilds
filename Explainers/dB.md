# deciBels

This file explains decibels, typically abbreviated to dB.

Before explaining dB, I want to dispel some conceptions of dB that you may bring to RF engineering.

First, dB is not a unit. If I write 6V, I mean that there is a unit of voltage and that there are 6 of these. But 6dB does not mean that there is a unit called dB and there are 6 of them. It is much more akin to percent. Percent is not a unit. Percent is not a unit. It is a way to express a number, typically between 0 and 1, as an integer.

The dirty little secret of human frailty is that we have a much easier time tracking integers in our head than non-integers. For example it is much easier to add 5 and 8 to get 13 in your head than to add 0.5 to 0.8 to get 1.3. They are the same thing, except the second one has an extra decimal point. But that extra decimal point adds cognitive load. The 'cent' in percent means hundred. The 'per' part makes it mean hundredth. The dec in decibel means tenth. The Bel part....

So let's table this for a small bit. In RF engineering, it is very often the case that we design circuits by cascading subcircuits together. These subcircuits take inputs and produce outputs. More or less. The effects of each subcircuit is often multiplicitive. Thus, it is often the case that we want to multiply the effects at a bunch of stages. So if the first part is x8 and then it goes into a x12, what do we have? x96. Now run that into a x3. Now what is it? Sure, you can keep track in your head, sort of.

But thanks to logarithms, we can drop into log-base-10 world and instead of multiplying, we can just add numbers together. The human brain handles adding so much better than multiplying.

However, the sort of resolution of we need requires us to add numbers that are accurate to about 0.1. Recall from above, that 0.5 + 0.8 == 1.3 is harder to do than 5 + 8 == 13.

So, if we take the log of a number and multiply it by 10, we get low cognitive load integers.

The second conception is that dB is NOT an absolute measurement. If you don't do much radio, your exposure to dB is probably in sound measurement where dB is an absolute value of the level of sound. But in RF, dB is a measure of relative multiplication. We often say x dB up to indicate that we are adding (i.e. multiplying) or X dB down to indicate division.

Let's take an example to clarify a bit. Say I have an amplifier that multiplies a signal by 25 times. So if the input power is 0.01W, the output is 0.25W. The text book definition will be 10*log(Vout/Vin). So you would take 25, take the log-base-10, then multiply by 10, and that is the dB.

Now, when presented with this formula, our first instinct might be to whip out our phone and pull up our favorite scientific calculator app and enter 25, then press the log-10 button, and multiply that by 10.


So if the input voltage is 0.01V peak to peak, the output is 0.25V peak to peak. The text book definition will be 20*log(Vout/Vin).

# 10 and 3

Older RF engineers who grew up with slide rules know something really cool. log10(2) is really really close to 0.3. (They also know that log10(pi) is really close to 0.5.) There are some advantages that the pre-digital world engineers have and the intuitions that come from usage of the slide rule is one. But now we are in the digital age and digital age people have an intimate knowledge of powers of 2.

If you are digital-centric, go to an antique store and get a slide rule and play with it. If you aren't digital centric, learn the powers of 2 from like .0625 to 1024.

So onto the title of this section 10 ansd 3.

First 10dB up means times 10. 10dB down means divide by 10. So what's 10dB up? It's NOT times 20. It's 10dB up and then another 10dB up. So its times one hundred. 30dB up is times a thousand. 20dB down is one hundredth. 30dB down is one one thousandth.

Next, we take advantage of the fact that log(2) is 0.3 (i.e. 10*log(2) is about 3) to say that 3 dB up means you double something. 3dB down means you halve something. 6dB up? Two doublings or times 4. 9dB down? one eighth.

All you need to know to do quick and pretty good dB conversions in your head are these 2 numbers.

# dB to Multiplier

Say you have a dB value and you want to convert it from dB to the equivalent power multiplier and you don't want to take out your calculator. Are you sunk? Not at all!

Assuming we are dealing with integers. If you need more accuracy than that, then you need your calculator.

But let's go. A dB value is typically going to be an integer in the -100 to 100 range. Actually even that is really wide. But they will typically numbers in teh range where humans handle integers really well.

The first thing to do is to rewrite the integer as the sum of a multiple of 10 plus or minus a low multiple of 3. By low multiple of 3, I mean roughly -12 to 15.

## Try it:
```
14 is 20 - 6
15 is 0 + 15
16 is 10 + 6
17 is 20 - 3
-5 is 10 - 15
-8 is -20 + 12
```

See what's going on? First number is a multiple of 10, and the second is a multiple of 3. Pick some random integers and express them as the sum of a multiple of 10 and a low multiple of 3. You'll see that it's pretty easy.

## The Multiple of 10

First take the multiple of 10. Divide it by 10. So 10 becomes 1, -10 becomes -1, 30 becomes 3. So simple.

Take 10 to the power of that. So 10 leads to 10, -10 leads to 0.1, 0 leads to 1, 30 leads to 1000.

The great thing about multiples of 10 is that they are just ways of moving the decimal point around.

## The multiple of 3

Now, take the multiple of 3 and divide by 3. So 6 becomes 2. -9 becomes -3.

Do you recall your powers of 2? Let's just refresh them:
```
-4: 0.0625
-3: 0.125
-2: 0.25
-1: 0.5
0: 1
1: 2
2: 4
3: 8
4: 16
5: 32
```

## Combining them
So now it's just a matter of taking the power of 2 you got from the multiple of 3 and adjusting the decimal point with the power of ten. There are a few ways to do this quickly in your head and I invite you to play in you head and decide the easiest way for you to multiply the power of 10 with the power of 2 accurately. I like to start with the multiple of ten and double or halve the appropriate number of times.

So let's take 14dB. 14 is 20 - 6. So the 20 means we start at 100 and -6 means we halve twice. A quarter of 100 is 25. So 14dB is 25x.

Wow! That was easy, no? And you didn't need to whip out your calculator! I do need to warn you a warning a cetain yoga instructor told us after showing us a particular difficult pose--these are not party tricks. But if you pick up some cutie by converting dB into a multiplier--well all's fair in love and war.

# Multiplier to dB

You can use the same technique going back from a multiplier to dB, but I have a slightly different method. The dB to multiplier method is easy for me, but I do have to keep track of the decimal point. My prefered way to go the other makes the decimal point something I don't have to worry about. Again YMMV and id you think my method is stupid and a variant is much better, then absolutely use the easier one. The point of these exercises is to enable compenent use of dB doing conversion quickly in your head without needing a calculator. The method that maximizes your ability to do that is the method you want to use for yourself.

So say you have a number that is a multiplier that you want to convert to dB...

## Ab.c dB

My method for finding Ab.c dB is outlined here. Note that the `c` part is sort of optional and depends on a linear interpolation.

Finding the A part is simple. Take your multiplier and round donw to the nearest power of 10. Count the number of 0's. If the number is less than one, make the number negative and count the zero to the left of the decimal point. If you studied logarithms at all, this should be pretty intuitive.

The next part needs a little explanation but is really easy once you see the pattern. Now that we have `A` we don't need to worry about the exponent part of the mantissa. It's just all mantissa. And for that we have the left justified sig figs of the powers of 2 in a decade. I use -4 to 5. So let's write out the sig figs without the exponent for -4 to 5. You'll see what's going on, I swear:

```
625
125
25
5
1
2
4
8
16
32
```
So, what you want to do is sort of rearrange this list in your head to this.

```
1
125
16
2
25
32
4
5
625
8
10
```

Now find the left justified mantissa that is lower than your number in this list. The ordering method is a little weird, but you'll get used to it quickly. Also find the next higher number.

So now, you have these 2 numbers. So you know the exponent you raise 2 to get those numbers, right. So if your number was 42000, then it's a little higher than 4 and and little less than 5, right?

4 is 2^2 and 5 is 2^-1.

Now take the exponents> 2 and -1, in this example. And multiply them by 3. If the number is negative, add 10 until it's positive again.

Got that number? The ones digit is `b`.

OK, that result to get `b` is pretty unintuitive. I'll make a slide rule video that shows this, though.

If you want `c` then it's pretty reasonable to do a linear interpolation. The nice thing about dB is that the resolution at integer level is good enough for calculations you're doing in your head without use of a calculator. But if you really want a little more resolution, then you can do an interpolation with 2 digits of the the list above, and the 2 most signifacant digits, you can do a pretty reasonable `c`.