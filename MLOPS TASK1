from io import BytesIO
import json
import random
import cv2
from keras.models import load_model
import numpy as np
from keras.preprocessing import image
model = load_model('C:/Users/lenovo/Desktop/mask_face/maskmodel.h5')
face_cascade = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')


def face_extractor(img):
    faces=face_cascade.detectMultiScale(img, scaleFactor=1.3, minNeighbors=5)
    
    if faces is ():
        return None
    for (x,y,w,h) in faces:
        cv2.rectangle(img,(x,y),(x+w,y+h),(0,255,255),2)
        cropped_face = img[y:y+h, x:x+w]


    return cropped_face
video_capture = cv2.VideoCapture(0)
while True:
    _, frame = video_capture.read()
    face=face_extractor(frame)
    if type(face) is np.ndarray:
        face = cv2.resize(face, (224, 224))
        im = Image.fromarray(face, 'RGB')
        img_array = np.array(im)
        img_array = np.expand_dims(img_array, axis=0)
        pred = model.predict(img_array)
        print(pred)                   
        name="None matching"
        
        if(pred[0][0]==0.):
            name='Mask On'
            cv2.putText(frame,name, (50, 50), cv2.FONT_HERSHEY_COMPLEX, 1, (0,255,0), 2)
        else:
            name='Mask Not On'
            cv2.putText(frame,name, (50, 50), cv2.FONT_HERSHEY_COMPLEX, 1, (255,0,0), 2)              
    else:
        cv2.putText(frame,"No face found", (50, 50), cv2.FONT_HERSHEY_COMPLEX, 1, (0,155,45), 2)
    cv2.imshow('Video', frame)
    if cv2.waitKey(2)==27:
                break 
   
video_capture.
