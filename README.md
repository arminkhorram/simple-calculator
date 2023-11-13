# simple-calculator
This is a simple calculator with Kivy

First install the Kivy library.
Copy and paste this command in your code editor's terminal
'pip install kivy'

Then copy and paste the following code:

# Importing Kivy modules
from kivy.app import App
from kivy.uix.gridlayout import GridLayout
from kivy.uix.button import Button
from kivy.uix.textinput import TextInput

# Creating the Calculator Layout
class CalculatorLayout(GridLayout):
    def __init__(self, **kwargs):
        super(CalculatorLayout, self).__init__(**kwargs)
        self.cols = 4  # We'll have 4 columns for our calculator buttons


# Adding Buttons to the Layout
    def add_button(self, label, on_press):
        button = Button(text=label, on_press=on_press)
        self.add_widget(button)

# Populating the Grid with Buttons
        for i in range(1, 10):
            self.add_button(str(i), self.on_button_press)
        self.add_button('C', self.clear_input)
        self.add_button('0', self.on_button_press)
        self.add_button('=', self.calculate_result)
        self.add_button('+', self.on_button_press)
        # Add more buttons as needed


# Handling Button Press Events
    def on_button_press(self, instance):
        current_input = self.ids['input_box'].text
        new_input = current_input + str(instance.text)
        self.ids['input_box'].text = new_input

    def clear_input(self, instance):
        self.ids['input_box'].text = ''

    def calculate_result(self, instance):
        try:
            result = eval(self.ids['input_box'].text)
            self.ids['input_box'].text = str(result)
        except Exception as e:
            self.ids['input_box'].text = 'Error'



# Main App Class
class CalculatorApp(App):
    def build(self):
        return CalculatorLayout()

# Running the App
if __name__ == '__main__':
    CalculatorApp().run()
  
