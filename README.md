import cv2

video = cv2.VideoCapture(r"C:\Users\berra\Downloads\cute_animals.mp4")

#rgb kodu 
def show_rgb(event, x, y, flags, param):
    if event == cv2.EVENT_LBUTTONDOWN:  
        b, g, r = frame[y, x]  
        print(f'RGB değerleri ({x}, {y}) konumunda: ({r}, {g}, {b})')

cv2.namedWindow('Video')
cv2.setMouseCallback('Video', show_rgb)

#pause
paused = False
while True:
    if not paused:
        ret, frame = video.read()
        if not ret:
            print("Reached end of video.")
            break

        cv2.imshow('Video', frame)

    key = cv2.waitKey(40) & 0xFF
    if key == ord(' '): 
        paused = not paused
    
    if key == ord('q'): 
        break

video.release()    
cv2.destroyAllWindows()
