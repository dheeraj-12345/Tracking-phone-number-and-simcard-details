# Tracking-phone-number-and-simcard-details
rom tkinter import *
from phonenumbers import parse, carrier, geocoder
# Tkinter instance
tKinter = Tk()
# Set up the window size
tKinter.geometry("500x500")
# Phone number entry
number = Text(highlightcolor="yellow", width=20, height=1, wrap=WORD)
# .pack() is used to build the window
number.pack()
# Function to get the phone number details
def show():
    # Get the phone number from the text box entry
    phNumber = number.get('1.0', END)
    # Parse the phone number. pasrse() was called from phonenumbers library
    phNumber = parse(phNumber)
    # Get the Location details
    description = geocoder.description_for_number(phNumber, "en")
    # Get the Carrier/Provider details
    carrierName = carrier.name_for_number(phNumber, "en")
    # Config the text property of the [Label] widget
    phResult.config(text= str(phNumber) + "\nDescription: " + description + "\nCarrier: " + carrierName)
 
# A built Button to get the phone number details
Button(text="Submit", command=show).pack()
 
# A Label to display the phone number details
phResult = Label(height=10)
 
# .pack() is used to build the Label widget
phResult.pack()
 
# Run the main loop of the Tkinter to display the window
tKinter.mainloop()
