>Report of Robot Software Engineering 
  Our group prepares to make a smart bartender robot based on the Restaurant part of the Robocup 2019 rule. The goal is to complete the voice command giving by someone and go to the target location. Then the robot uses his robotic arm to grasp a cup of coffee or tea and navigate back to the start location autonomously. And then the robot should hand what he is catching to the customer.
  Our innovation is: When the robot recognizes the customer's beckoning action, he uses the voice to actively ask the customer's needs and communicate with the customer to meet the customer's needs.
  I am responsible for the voice part of the robot. What I want to realize is that the robot can communicate with the customer, and recognize the commands which the customer give. He should know the needs of the customer and then execute, and then use the other modules to achieve the overall function.
  The process of robotic action:
When the robot recognizes the customer's beckoning action, he would say “Yes, I’m coming.” Then he would navigate to the customer.
In this section, our group use Baidu API to identify the posture of the customer’s body. When the robot did it, we would publish a message of “Yes, I’m coming.” to the topic “speech” and the robot would say this sentence. And then Then he would navigate to the customer. But the delay of the Baidu API is long, we can only receive the position of the previous second. So, he walked a little shaking. There was an idea that we only use the Baidu API for recognizing the posture of the customer’s body and the use dlib or some other packages to track the customer’s body. But he's still not running smoothly. And now this problem has not been solved well. 
When he arrived at the customer, he would ask the customer “Hello! What do you want to drink, coffee or tea?”
      In this section, we will set a suitable distance between the robot and the customer.
Then the customer would tell his needs to the robot. The robot would recognize the commands which the customer give and then navigate to the bar .

The next step is that the robot uses his robotic arm to grasp a cup of coffee or tea and navigate back to the start location autonomously.
In this section, I came up with an idea that we can use PID Controller to adjust the position of the end of the arm to grasp the coffee or tea. And I wrote an algorithm for a PID controller. I want the robot to go to the same position near the bar every time. Then we could use the PID controller to control x, y, z respectively. And what we need to control is the angles (The formula about coordinate and angles is known).But there are a better way to let the robot arm grasp more accurately. The method is that we can use navigation to let the robot be the same distance from the bottle every time and then grasp the bottle.
‘’’
PID
‘’’

Then the robot would band what he is catching to the customer and say “Here is your …. Enjoy yourself.”
The Implementation of the voice part:
Define a talk function in main.py:
def talk(text):
    pub = rospy.Publisher('speech', String, queue_size=10)
    time.sleep(0.1)
pub.publish(text)  
 Then modify say.py
 //copy the say.py here
First, when Baidu API recognizes the customer's beckoning action, it will publish a message and then execute 
‘’’
talk (“Yes, I’m coming.”)
‘’’’

Second, when it receives the message of “finding_finish”, it would execute
‘’’
talk ("Hello! What would you like to have? Coffee or tea?")
‘’’

Third, when it receives the message of “navi_finish”, it would execute
‘’’
talk ('Here is your' + drink + '. Enjoy yourself.')
‘’’
Summary and outlook:
   In this assignment, our final robot has generally met our initial expectations. My task in my group is relatively simple. So, I paid some attention to the visual and mechanical arm parts. I have some thoughts on the robotic arm and the visual aspect, though some of my ideas were replaced by some better ways. But I think that I grew up in this assignment. I understood a lot of knowledge about robots and I recognized many methods. I hope that in the future I can learn more about robots. At last, thank you teacher for your care during this semester. You helped me learn a lot of knowledge about robots. Thank you very much.
