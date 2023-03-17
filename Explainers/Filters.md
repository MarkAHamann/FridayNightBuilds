# Filters

There are 2 fundamental types of filters. Low pass and high pass. You often hear of notch filters and band pass filters but they are really just sort of low pass and high pass filters superimposed on each other in a sort of cascade.

When I was taking basic circuits, the class quickly went into filters after capacitors with essentially no context as to what a filter is. We studied filters from a purely time domain point of view because the math we had for RC circuits was time domain math. And our initial forays into filters with time constants was with DC step functions.

Without context, I knew there was a thing called a filter and that it did something, but I had no idea that what it did was so simple. The problem is that it is only simple if you approach filters from a frequency domain point of view. Studying filters from a time domain point of view is useful only to 2 groups:
1) people who haven't been exposed to frequency domain and only have the math for time domain analysis
2) people who understand filters extemely well and need to look at time domain to deepen their understanding.
One of these types is legitimate. I was the other type.

I have a section on frequency domain. If you aren't familiar with frequency domain, then you'll want to check that out now. Don't fall into the same trap I fell into by not knowing what frequency domain is.

## Human scale time constants and a scope

Let's start with the RC filter. The RC filter is easy to understand because it has only one energy storage element. It's not intuitive now but the more energy storage elements in a filter the more complex it is.

Anyway, with a resistor and capacitor, there are 2 configurations of filter.

1) signal comes into the resistor then the capacitor to ground and the output comes out between the resistor and capacitor.

2) signal comes into the capacitor then the resistor to ground and the output comes out between the resistor and capacitor.

While this seems like they might be similar, they are actually really different. The first one is a low pass filter and the second is a high pass filter.

The way to understand which filter is low an which is high pass, is to understand that capacitors change relatively slowly. The voltage across the capacitor will change slowly. So if the capacitor is the lower part, high frequency changes will be absorbed by the capacitor, but slower changes will cause the capacitor to charge or dischange. Vice versa with the capacitor in the upper part.

Let's play with a circuit connected to an oscilloscope. As it happens, I have a 2 channel scope but the differences might be more obvious in a 4 channel scope where you can see the signal, low pass output, and high pass output.

If we decide on a time constant of about 1 second, we can see in slow motion what filters do and get an intuitive idea of what they do.

The thing to notice is that if you look at the input and output of the low pass filter, you can see that slow movements on the input cause the output to follow them. The output wants to get to the input, but it takes time.

In the case of the high filter, you can see that the output wants to be be 0v. Slow changes may have a littl effect on the output. But not much. But try a quick sudden change and it shows up really well before the output settles back to 0 volts. It's sort of like predators that only see movement so that if you don't move they can't see you.

So, the result is that you'll see that the output of the low pass filter is good at following the input when the input moves slowly and the high pass filter is good at following the output when the output moves quickly.

Now we can do something neat. We can do a sine wave frequency sweep of the 2 filters that starts slow and ends fast with espect to the filters. When the frequency of the sine wave is really low, the output of the low pass filter shows the sine wave because it's good at tracking slow stuff. When the sine wave frequency is high, the low pass filter just sort of gets the average of the sine (zero) while the high pass filter shows the sine wave. In between, there is a point where both sort of do an ok job of passing the signal.

This makes it easy to see how the filter affects the amplitude. A filter has another important component, though. That is phase shift. This is a little harder to intuit because AC signals are just plain harder to understand than DC signals. But you can see that voltages, as they try to catch up to the input, but fall short, fall short somewhat consistently. You can see that the output peaks are not in the same place as the input peaks when the output is not keeping up witht he inputs. If you take peak to peak as 2*pi or 360 degrees, you can see that the output leads or lags by some portion of that period. That is the phase shift. The phase shift depends on the frequency.

When you have an amplitude that depends on frequency and you have a phase shift that depends on frequency, you can construct what is called a Bode (bow dee) plot. The Bode plot is easist to construct with simple rules when you understand dB. See the section on dB for an explanation of dB.





