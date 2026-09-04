# guess-number-with-timeout
python programming and project 
import threading
def input_with_timeout(prompt,timeout=50):
    result=[None]
    def get_input():
        result[0]=input(prompt)
    thread=threading.Thread(target=get_input,daemon=True)
    thread.start()
    thread.join(timeout)
    if thread.is_alive():
        print('You ran out of time')
        return None
    else:
        return result[0]
import random
number_to_guess=random.randint(1,100)
guesses=0
while True:
    user_input=input_with_timeout('Guess a number between 1and 100')
    if user_input is None:
        print('You ran out of time')
    elif user_input=='':
        print("You did not enter anything")
    else:
        try:
            guess=int(user_input)
            guesses+=1
            if guess>number_to_guess:
                print("Too High")
            elif guess<number_to_guess:
                print("Too Low")
            else:
                print("Congratulations You guess the number correctly")
                print(f'This round took you {guesses} guess/es')
                should_continue=('Continue to play again? (y/n)').lower()
                if should_continue!='y':
                    print('bappa krishna')
                    break
        except ValueError:
            print("Enter valid number")
