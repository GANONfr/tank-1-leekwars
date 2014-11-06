tank-1-leekwars
===============

pour jouer en team full puces

var moi = getLeek();
var enemy = getNearestEnemy();
var nomEnemie = getName(enemy);
var maCellule = getCell();
var saCellule = getCell(getNearestEnemy());
var distance = getCellDistance(maCellule, saCellule);
var force;
var deplacement;
var saVie = getLife(enemy);
var soinFaible;
var soinFort;
var defenseFaible;
var boostAgilite;
var mur;

if (saVie < 130 and distance ==1) {
	setWeapon(WEAPON_MACHINE_GUN);
	useWeapon(enemy);
	useWeapon(enemy);
}





if (getAlliesCount()  >= 1 and distance > 1 and (saVie = (saVie/2)) and getLife() > 155) // on est en équipe
{
	deplacement = moveToward(enemy);
	useChip(CHIP_ICE, enemy);
	useChip(CHIP_ROCK, enemy);
	//say("Viens voir papa " + nomEnemie);
	
}
if (getAlliesCount() >= 1 and deplacement <= 0 ) {

	boostAgilite = useChip(CHIP_STRETCHING, moi); //retourne 1 juste après avoir réussit et -3 après pendant 3 tours
	soinFort = useChip(CHIP_CURE, moi); //1 fois 1 et 1 fois -3
	soinFaible = useChip(CHIP_BANDAGE, moi); //1 à chaque fois
	defenseFaible = useChip(CHIP_HELMET, moi); //retourne 1 juste après avoir réussit et -3 après pendant 3 tours
	
}
if (getAlliesCount() >= 1 and soinFort == 0)//si fail puce
{
	soinFort = useChip(CHIP_CURE, moi);
}
if (getAlliesCount() >= 1 and defenseFaible == 0)//si fail puce
{
	defenseFaible = useChip(CHIP_HELMET, moi);//si fail puce
}
if (getAlliesCount() >= 1 and soinFaible == 0)
{
	soinFaible = useChip(CHIP_BANDAGE, moi);
}

if (getAlliesCount() >= 1 and soinFort == -3)//quand puce cure est en cooldown
{
	mur = useChip(CHIP_WALL, moi);
}

if (getAlliesCount() >= 1 and mur == -3)//quand cure est mur sont cooldown
{
	useChip(CHIP_ICE, enemy);
	
}
if (getAlliesCount() >= 1 and defenseFaible == -3)//quand helmet est cooldown
{
	useChip(CHIP_ICE, enemy);
}
