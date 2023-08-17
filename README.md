# Real-Time-Lane-Detection

Searching the Internet...


In this code i've tried to draw lane lines in a video. It uses the OpenCV library, which is a popular computer vision library, to perform various image processing operations.

## Installation

To run this code, you need to have OpenCV installed. You can install it by following the instructions on the OpenCV website (https://opencv.org/).

## Usage

To use this code, follow these steps:

1. Import the necessary libraries:
   - `import cv2` to use OpenCV for image processing.
   - `import numpy as np` to work with arrays and matrices.

2. Define the `get_lanes` function:
   - This function takes a video source as input and returns the detected lane lines and the region of interest (ROI).
   - It reads the first frame of the video and allows you to select a ROI using the keyboard.
   - It crops the ROI from the first frame and performs some image processing operations on it.
   - It applies dilation to increase the size of white color in the image.
   - It converts the image to grayscale and thresholds it to get only white colors.
   - It uses edge detection to find lane lines in the image.
   - It returns the detected lane lines and the ROI.

3. Test the `get_lanes` function:
   - In the `if __name__ == '__main__'` block, specify the path to the video you want to process.
   - Create a `VideoCapture` object to read the video.
   - Call the `get_lanes` function to get the lane lines and ROI.
   - Iterate through the frames of the video.
   - If lane lines are detected, draw them on the frame.
   - Display the output frame.
   - Press 'q' to exit the program.

## Example

Here's an example of how to use this code:

```python
video_path = "1.mp4"

video = cv2.VideoCapture(video_path)
lines, r = get_lanes(video_path)

while True:
    check, frame = video.read()
    if check == False:
        break

    # draw line
    if lines is not None:
        for line in lines:
            x1, y1, x2, y2 = line[0]
            cv2.line(frame, (x1+ r[0], y1 + r[1]), (x2 + r[0], y2 + r[1]), (0, 255, 255), 3)

    # Display output
    cv2.imshow("Demo", frame)
    if cv2.waitKey(5) & 0xFF == ord('q'):
        break

video.release()
cv2.destroyAllWindows()
```

In this example, the code reads a video file named "1.mp4" and detects the lane lines in each frame. It then draws the detected lane lines on the frames and displays the output in a window. Press 'q' to exit the program.

## Contributing

If you have any suggestions or improvements for this code, feel free to contribute. You can submit a pull request or open an issue on the GitHub repository (link to the repository).
