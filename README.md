# Trivia_Game_Beginner
Just a trivia game with UI made with Tkinter. It is not perfect, so if you can correct anything you see wrong, please do.
#import necessary modules
import tkinter
from time import sleep
#create empty score list 
global score
score = []
#write questions and answers. you also create the buttons for the widget
questions = {
    1: {
        1: "Which Doctor had the chance to kill Davros?",
        "o1" : "The 4th",
        "o2" : "The 11th",
        "o3" : "The 6th",
        "ans": "The 4th"
        },
    2: {
        2: "In anime, what frase is usually said after 'omae wa mo shindeiru!'?",
        "o1" : "Shine!",
        "o2" : "Nani?!",
        "o3" : "I don't know",
        "ans": "Nani?!"
        },
    3: {
        3: "Complete the phrase: 'Remember remember...'",
        "o1": "the fifth of november",
        "o2": "the sounds of december",
        "o3": "Don't know",
        "ans": "the fifth of november"
        },
    4: {
        4: "Who is the Paranoid Android?",
        "o1": "C3P0",
        "o2": "Marvin",
        "o3": "Wall-E",
        "ans": "Marvin"
        },
    5: {
        5: "Which trainer was Goku's second trainer?",
        "o1": "Master Jiraiya",
        "o2": "Master Roshi",
        "o3": "Yokio Okumura",
        "ans": "Master Roshi"
        },
    6: {
        6 : "Djent is defined by ",
        "o1": "Changing styles of singing",
        "o2": "Heavy palm-muted riffs",
        "o3": "Using 7 or 8 string guitars",
        "ans": "Heavy palm-muted riffs"
        },
    7: {
        7: "What is Entomology?",
        "o1" : "The study of insects",
        "o2" : "The study of words",
        "o3" : "The study of plants",
        "ans": "The study of insects"
        },
    8: {
        8: "What is Apeirophobia?",
        "o1" : "Fear of pain",
        "o2" : "Fear of the endless",
        "o3" : "The fear of failure",
        "ans": "Fear of the endless"
        },
    9: {
        9: "What are the main characters' names in Terror in Resonace?",
        "o1" : "5 and 12",
        "o2": "12 and 9",
        "o3": "9 and 5",
        "ans": "12 and 9"
        },
    10: {
        10: "What is the capital of Japan",
        "o1" : "Kyoto",
        "o2": "Sapporo",
        "o3": "Tokyo",
        "ans": "Tokyo"
        },
    11: {
        11: "In which of Plato's dialogues does the allegory of the cavern appear?",
        "o1" : "The Republic",
        "o2": "Phedon",
        "o3": "Symposium",
        "ans": "The Republic"
        },
    12: {
        12: "Ok. You are done. Press END",
        "o1" : "Dont press Submit",
        "o2": "Capisce?",
        "o3": "Press end",
        "ans": ""
        }
    }


#pretty self explanatory
def end():
    main.destroy()



#here you keep track of the questions which have already been asked. in this case no questions have passed, but you add one to ask the first question    
global questions_passed
questions_passed = ["-"]


#this is probably a bad name for the function, because this changes the widget to the corresponding text and checks the answer the user chooses
def check_answer():
    global questions_passed
    global score
    option = optionw.get()
    #defines the answer
    answer = questions[len(questions_passed)]["ans"]
    #updates widget. the only change compared to the else below is the score
    if option == answer:
        score.append("lsdf")
        questions_passed.append("seg")
        sleep(1)    
        question["text"] = questions[len(questions_passed)][len(questions_passed)]
        rb1["text"] = questions[len(questions_passed)]["o1"]
        rb1["value"] = questions[len(questions_passed)]["o1"]
        rb2["text"] = questions[len(questions_passed)]["o2"]
        rb2["value"] = questions[len(questions_passed)]["o2"]
        rb3["text"] = questions[len(questions_passed)]["o3"]
        rb3["value"] = questions[len(questions_passed)]["o3"]
        scorep["text"] = "Score: " + str(len(score)) + "/" + str(len(questions)-1)
    else:
        score = score
        questions_passed.append("1")
        sleep(1)
        question["text"] = questions[len(questions_passed)][len(questions_passed)]
        rb1["text"] = questions[len(questions_passed)]["o1"]
        rb1["value"] = questions[len(questions_passed)]["o1"]
        rb2["text"] = questions[len(questions_passed)]["o2"]
        rb2["value"] = questions[len(questions_passed)]["o2"]
        rb3["text"] = questions[len(questions_passed)]["o3"]
        rb3["value"] = questions[len(questions_passed)]["o3"]
        scorep["text"] = "Score: " + str(len(score)) + "/" + str(len(questions)-1)
        
#create widget
global main
main = tkinter.Tk()
question = tkinter.Message(main, text = questions[len(questions_passed)][len(questions_passed)], width = 150)
question.grid(row = 0, column = 1)
global optionw
optionw = tkinter.StringVar()
rb1 = tkinter.Radiobutton(main, text = questions[len(questions_passed)]["o1"], variable = optionw, value = questions[len(questions_passed)]["o1"])
rb1.grid(row = 1, column = 0)        
rb2 = tkinter.Radiobutton(main, text = questions[len(questions_passed)]["o2"], variable = optionw, value = questions[len(questions_passed)]["o2"])
rb2.grid(row = 1, column = 1)
rb3 = tkinter.Radiobutton(main, text = questions[len(questions_passed)]["o3"], variable = optionw, value = questions[len(questions_passed)]["o3"])
rb3.grid(row = 1, column = 3)
submit = tkinter.Button(main, text = "Submit", command = check_answer)
submit.grid(row = 2, column = 1)
scorep = tkinter.Label(main, text = "Score: " + str(len(score))  + "/" + str(len(questions)-1))
scorep.grid(row = 3, column = 1)
end = tkinter.Button(main, text = "End", command = end)
end.grid(row = 4, column = 2)
main.mainloop()
        
