# SFND_Radar
4th Project in the SFND program from Udacity
## Project Layout
<img src="/images/project_layout.png"/>

## Project Output
<img src="/images/Output.PNG" />

## Implementation steps for the 2D CFAR process

- Chose values for x & y directions which is equivalent to range and doppler dimensions.

```
Tr = 12;
Td = 8;
```

- Guard cells in x &  y directions.
```
Gr = 4;
Gd = 4;
```


- Offset.
```
offset = 1.2;
```
- A loop that goes through all the cells under test in Range-Doppler Map (refered to as RDM)
- In each iteration , it adds the signal level in the training cells , uses the function dp2pow to convert the value from logarithmic to linear.
- Average all the summed values and then converting it back to logarithmic form using the function pow2db.
- Adding the offset to the average to determing the threshold.
- Compare the signal under CUT with the calculated threshold , if the CUT level is less than threshold , assign the value to 0 , else assign to 1.

<img src="/images/CFAR.PNG" />

## Steps taken to suppress the non-thresholded cells at the edges
The process above will generate a thresholded block, which is smaller than the Range Doppler Map as the CUT cannot be located at the edges of matrix. Hence,few cells will not be thresholded. To keep the map size same set those values to 0.

<img src="/images/nth.PNG" />
