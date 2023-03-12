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

See what's going on? First number is a multiple of 10, and the second is a multiple of 3.

## The Multiple of 10

First take the multiple of 10. Divide it by 10. So 10 becomes 1, -10 becomes -1, 30 becomes 3. So simple.

Take 10 to the power of that. So 10 leads to 10, -10 leads to 0.1, 0 leads to 1, 30 leads to 1000.

The great thing about multiples of 10 is that they are just ways of moving the decimal point around.

## The multiple of 3

Now, take the multiple of 3 and divide by 3. Sop 6 becomes 2. -9 becomes -3.



# Multiplier to dB
