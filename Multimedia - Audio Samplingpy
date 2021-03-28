import tkinter as tk
from tkinter.filedialog import askopenfilename
import pyaudio
import wave
import sys

class Application(tk.Frame):
    def __init__(self, master=None):
        super().__init__(master)
        self.master = master
        self.pack()
        self.create_widgets()
        #self.filee = None
        #self.printfile()
        #self.Slow()
        #self.Normal()
        #self.Fast()
        #self.Play(0)

    def create_widgets(self):
        self.hi_there = tk.Button(self)
        self.hi_there["text"] = "Open"
        self.hi_there["command"] = self.openfiledialog
        self.hi_there.pack(side="top")
        
        self.slow = tk.Button(self, text="Slow", command=self.Slow)
        self.slow.pack(side="top")

        self.normal=tk.Button(self,text="Normal", command=self.Normal)
        self.normal.pack(side="top")

        self.fast = tk.Button(self, text ="Fast", command=self.Fast)
        self.fast.pack(side="top")
        self.quit = tk.Button(self, text="QUIT", fg="red",
                              command=self.master.destroy)
        self.quit.pack(side="bottom")

    def openfiledialog(self):
        self.filee = askopenfilename(filetypes=(("wave","*.wav"),("All Files","*.*")))
        
    def Slow(self):
        self.Play(30000)
    def Normal(self):
        self.Play(45000)
    def Fast(self):
        self.Play(60000)
    def Play(self, samplerate):

        wf = wave.open(str(self.filee), 'rb')
        p = pyaudio.PyAudio()
        stream = p.open(format=p.get_format_from_width(wf.getsampwidth()),
                channels=wf.getnchannels(),
                rate=samplerate,
                output=True)
        data = wf.readframes(1024)
        while len(data) > 0:
            stream.write(data)
            data=wf.readframes(1024)
        
        stream.stop_stream()
        stream.close()
        p.terminate    
    #def printfile(self):
       # print(self.filee)

root = tk.Tk()
app = Application(master=root)
app.mainloop()
