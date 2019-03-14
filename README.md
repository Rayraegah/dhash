# Perceptual hashing algorithm

Perceptual hashing algorithm is a general term for a class of algorithms, including aHash, pHash, and dHash. As the name suggests, perceptual hashing does not calculate hash values ​​in a strict way, but rather computes hash values ​​in a more relative way, because "similarity" or not is a relative decision.

| **algorithm** |       **hash**        | **speed** | **accuracy** |
| :-----------: | :-------------------: | :-------: | :----------: |
|     aHash     |     average hash      |   fast    |     low      |
|     pHash     |    perceived hash     |   slow    |     high     |
|     dHash     | difference value hash |   high    |     high     |

## Difference value hash (dHash)

Steps to compare images with dHash algorithm

1.  The fastest way to remove high frequencies and detail is to shrink the image. 72 pixels works best, so 9x8 is ideal dimensions
2.  Reduce the color of the image. Convert the image to a grayscale picture. This changes the hash from 72 pixels to a total of 72 colors.
3.  Compute the difference. The dHash algorithm works on the difference between adjacent pixels. This identifies the relative gradient direction. In this case, the 9 pixels per row yields 8 differences between adjacent pixels. Eight rows of eight differences becomes 64 bits.
4.  Assign bits. Each bit is simply set based on whether the left pixel is brighter than the right pixel. The order does not matter.

If the Hamming distance is less than 5, it is the same image.

### Usage

I use dHash algorithms to find reposts in the subreddits I moderate.

calculate the dHash value of an image

```python
hash = DHash.calculate_hash(image)
```

calculate the hamming distance between two images

```python
hamming_distance = DHash.hamming_distance(image1, image2)
```

calculate the hamming distance between two dHash values

```python
hamming_distance = DHash.hamming_distance(dHash1, dHash2)
```

## License

dHash algorithm is released under MIT license
