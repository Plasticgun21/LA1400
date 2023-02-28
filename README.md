# LA1400

import robocode.*;

// API help : https://robocode.sourceforge.io/docs/robocode/robocode/JuniorRobot.html

/**
 * BotMcBotface - a robot by Jeanneret Luca
 */
public void run() 
{
	setBodyColor(Color.blue);
	setGunColor(Color.green);
	setRadarColor(Color.blue);
	setScanColor(Color.green);
	setBulletColor(Color.blue);
	// Here I set the colours
	while (true) {
		turnGunRight(10); // This is that the turret turns forever, so it can scan enemys.
	}

	public void onScannedRobot(ScannedRobotEvent e) {
		double absoluteBearing = getHeading() + e.getBearing();
		double bearingFromGun = normalRelativeAngleDegrees(absoluteBearing - getGunHeading());
// Caculations for aiming at enemy.

		if (Math.abs(bearingFromGun) <= 3) {
			turnGunRight(bearingFromGun);
		
		if (getGunHeat() == 0) {
				fire(Math.min(3 - Math.abs(bearingFromGun), getEnergy() - .1));
			}
			// Caculation of the heat of the gun so it dosn't use all it's energy.
		} 
		else {
			turnGunRight(bearingFromGun); // If no robot is found, it will rescan.
		}
		
		if (bearingFromGun == 0) {
			scan(); // If not it will stop and move.
			foward(100);
		}
	}

	public void onWin(WinEvent e) {
	
	turnRight(69420); // ''Dances'' if it wins
	} 			
