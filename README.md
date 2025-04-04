# tubeRotator
A classic tube rotator to be used for what you desire to. In a pinch it could be used as a mini bioreactor.
Software is https://github.com/AdrianMolecule/OrbitalShakerMksBoard. Sorry for 2 repos but it seems to be the only way to do it decently in gitHub.
Normally can rotate 8 50 ml tubes and about 16 2 ml or 1.5 ml tubes in the same time from 0 to maybe 300 RPM before things start flying.

It takes a Nema 17 stepper but can be chaged for a more powerful (why I don't know) stepper which requires changing the hole positions in the rotor mount file.
By default the rotation is  80 RPM but it could be change to any value by using a serial terminal commands.
If you are interested I can also add a Wifi interface for changing speed and temperature.
It's tested and true.
Don't forget to leave tubes mostly empty if you want to grow e-coli. I normally use 1 to 2 ml LB media in a 10 ml tube. Don't forget that even then, the oxygen will almost ran out after about 7 hours.

Assembly Steps
Check your MKS board and the motor -Put in one stepper driver in the middle slot, connect power and serial port and then try the motor with the board separately first using the preinstalled MKS software and a CNC Laser cutter program like LaserGRBL. Check movement on Y axis.
Wire the board using the jumper cables, load our software on the board and try it after. If you want to do the driver current optimization described later after *.
Print parts without support in ABS if you can but I think PLA will work too. The template is just for marking where to drill the motor mounting holes but you can use the balljoint holder for that if you want.
Connect the desired holders with the rotor with screws or snap them with magnets
Assemble the rotating mechanical parts inside your box, try again
Print or get a board box, put the board supports, close the box and retry
Attach the board box to the main box.

BOM:
MKS DLC V?? with the cable for the serial port that normally comes with and at least one stepper driver ic that normally comes with. Better get the low noise one for obvious reasons.
6 mm rod. Mine came from either an old printer or a empty laser printer tonner cartridge.
6 mm internal diameter ball joint - Optional in case you want to support the shaft at both ends. I don't do that anymore!
6 mm to 5 mm shaft coupler. You can use a rigid one or the helice spring aluminium one. I tried both, the spring one is smoother at start depending on speed but I settled for the cheap fixed one. For example https://www.aliexpress.com/item/4000221326289.html?spm=a2g0o.order_list.order_list_main.5.2e7b18023d0EkV or https://www.aliexpress.com/item/4000589186252.html?spm=a2g0o.order_list.order_list_main.10.2e7b18023d0EkV
For holding the tubes you need either 8x 3 mm screws of about 15 mm or longer or 32 magnets of 12x6x2 mm.
More screws and nuts- all 3 mm 
4 x3mm screws for attaching the motor and at least 2 more for attaching the balljoint part. You need to determine the length based on how thinck you box is. 
Also at least 3 for attaching the MKS board box to your box and 4 more special screws to attach the MKS board to its box like https://www.aliexpress.com/item/33054086915.html?spm=a2g0o.order_list.order_list_main.151.2e7b18023d0EkV
Any Nema 17 stepper including flatter pancake ones like https://www.aliexpress.com/item/1005007016114666.html?spm=a2g0o.productlist.main.35.7f774895AlZWFk&algo_pvid=77c29ec8-36eb-487f-abc6-7f73ea85a693&algo_exp_id=77c29ec8-36eb-487f-abc6-7f73ea85a693-12&pdp_npi=4%40dis%21CAD%2113.28%2113.28%21%21%219.45%219.45%21%402103011017184219655302441e2644%2112000039081821468%21sea%21CA%21132308507%21&curPageLogUid=Vj7nNkeNSwOw&utparam-url=scene%3Asearch%7Cquery_from%3A
Options: you can use a bigger or smaller rod as long as the internal diam or the ball joint and one end of the shaft coupler mathes that bigger or samller diameter. So for instance 4 mm or 10 mm. You will also have to change the shaftDiam param inside the Fusion360 file and regenerate only the tube rotator (wheel) 3D printed file.
Some kind of enclosure about 250x190x-170mm, ideally with a door and partially transparent. Mine was an acrylic box from a water filter.
About 10 or less female to female pin connectors -2.54mm Dupont Line 20cm 10cm 40Pin  Female to Female like  https://www.aliexpress.com/item/32481623557.html?spm=a2g0o.order_list.order_list_main.69.e1ec1802BAvD1N
An old laptop adapter (mine is 18.5V) that matches the jack of the MKS board or you can either buy a jack adapter (you need to search for that so it matches your adapter and the MKS board) or you need to splice in a new jack after removing the original adapter jack. Could be anywhere from 12 V to about 25 V.
You can use the
Another short 3 mm screw in case the shaft hole does not hold the rod. Alternatively you can also use glue or just jam it with some tape on the rod
If you use magnets and they trend to come off their sockets you can also use glue.
I usually print in ABS whith no support and sometimes I use brims for holders in case it does not stick to the bed.
That is all for the rotator only part.

If you want the heater incubator part too:
You need need the power board a temperature sensor and a silicone heating pad of 12 or 24 volts. You will need to futher insulate the box in case you'll find that it takes too long to reach the desired temperature- usually 37 Celsius. You power the heat pad directly from the spindle (2 screws). I limited the max power to about 90%. It's important to put some metal holder under the heater otherwise it might melt the box. I used some tin leftovers fro some fascia cover but you can use a tin can. Careful when cutting it- use thick gloves.

No soldering should be required but 2 resistors need to be connected somehow, one is series with the piezo buzzer and one between + and signal pin on the temperature sensor. Their leads can be just spiralled around their connexion and electrical tape can be used for isolation. I did solder them and used shrink wrap for insulation but it's not necessary. As a matter of facts the buzzer itself could be considered optional.

**If you want to optimize the torque for the Nema motor, Google it on youTube. When using a noisier driver like DRV8825  watch=> https://www.youtube.com/watch?v=Vp9ZRCEhVYc . That could be different if you get the quiet driver so add the name of your driver to the Google search. I used the DRV8825 without noise issues.

At this point you can set the target RPM and target temperature using the serial port. Use CoolTerm (Free program) to connect to the serial port and type ? to see possible commands. At this point you can start stop the rotation, set the rotation speed and set the temperature. 
Sometimes on higher load depending on what motor you are using it migh not start until you give it a push with your finger. That is not necessary for me if I fully load the wheel with 50% filled tubes. Normally you will not fill the tubes more than 20% to have enough Oxygen but for other tasks that might not happen.

One simple way to accommodate smaller tubes is to put them in the 50 mm tubes with something to block them for moving (I use pieces of sponges)

Normally you get a faster delivery, better support on Amazon. All the links are just example and I encourage you to find beter one with better reviews, delivery, quality etc.
I built this as a quiter alternative to the orbital shaker. That's for making many glycerol stocks at the same time but it could be used for incubation or even as mini-bioreactor.

As with all projects, we looked at many existing devices and while we did not really copy anything from any of them there are natural similarities given the task. 

Special thank to Sebastian Cocioba who had published a similar device in OS. His designs are always true and his work is fantastic.
Update: the .stl files and the previous fusion360 show the model in the pictures that has been in use for a year or longer.

I just uploaded a new much slimmer model that also supports both screws or 5 mm cube magnets. As for the previous model you need at least 16 but better use 32 that gives you 8 large holders. The .stls are in the slimStls folder. This new model does not add new functionality but it's just much shorter to print.


I discovered that a short shaft that is only supported on the motor side is enough for rotation as long as the rotor is pushed closed to the motor. Sou don't need to print the orther end shaft support.
