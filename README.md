Denis
=====
public class SortTest {
	public static void main ( String [] args)
	{
		// создаем объект
		Sort peredacha = new Sort();
		// вызываем метод ввода размера массива
		peredacha.vvod();
		// запускаем цикл, для массива 60, 600 и 6 000
		for (int i=0;i<3;i++)
		{
		peredacha.quantity=0;
		System.out.println("Сортировка с помощью рекурсии:");
		peredacha.rekursia(0, peredacha.razmer);
		System.out.println("Количество замен для быстрой сортировки - " + peredacha.quantity);
		peredacha.vyvod();
		System.out.println("Сортировка с помощью пузырькового метода:");
		peredacha.bubbleSort(peredacha.razmer);
		peredacha.vyvod();
		System.out.println("Размер массива - " + peredacha.razmer);
		peredacha.razmer=peredacha.razmer*10;
		if (i>1)
			peredacha.razmer=peredacha.razmer*10;
		}
	}
}


public class Sort { 
	public static int razmer=100000;
	public static int[] mass = new int[razmer];
	public static int quantity = 0;
    
	public static void bubbleSort (int y)  {
	int[] mass = new int[y];
	// инициализация массива:
	for(int i=0; i<mass.length; i++)
		mass[i]=(int)(Math.random()*20);	
	// объявление переменной для подсчета
	int temp = 0;
	// сортировка элементов
	for (int i=0; i<mass.length; i++){
        for (int j=0; j<mass.length-1; j++){
            if(mass[j]>mass[j+1]){
            	int d=mass[j];
                mass[j]=mass[j+1];
                mass[j+1]=d;
                temp++;
            }
        }
    }
	System.out.println("Количество замен для пузырьковой сортировки - " + temp);
}
	
	public static void vvod ()
	{
		// класс для ввода данных с клавиатуры
		GameHelper helper = new GameHelper(); 
		String stringGuess = helper.getUserInput("Введите число"); 
		// класс Integer и метод parseInt для интерпритации stringGuess в int
		int guess = Integer.parseInt(stringGuess); 
		razmer = guess;
		// заполнение массива случайными числами
		for(int i=0; i<razmer; i++)
		mass[i] = (int)(Math.random()*20);	
	}
		
	public static void rekursia (int first, int last)
	{
		// создание объекта
		Sort peredacha = new Sort();
		
		if (first >= last)
 	 	 	return;
		// задаем переменные для выполнения сортировки с помощью рекурсии
 	 	int i = first, j = last;
 	 	int p = (i + j) / 2;
 	 	// цикл сравнения
 	 	while (i < j) {
 	 	 	while (( i < p ) && ( mass [i] <= mass [p] )) i++;
 	 	 	while (( j > p ) && ( mass [p] <= mass [j] )) j--;
 	 	 	if ( i < j ) {{
 	 	 		int temp = mass[i];
 	 	 		mass[i] = mass[j];
 	 	 		mass[j] = temp;
 	 	 	}
 	 	 	 	if ( i == p )
 	 	 	 	 	p = j;
 	 	 	 	else if ( j == p )
 	 	 	 	 	p = i;
 	 	 	}
 	 	}
 	 	// рекурсия
 	 	rekursia ( first, p );
 	 	rekursia ( p+1, last );	
 	 	// вызываем метод и прибавляем к нему 1
 	 	// будет служить для подсчета количества замен, выполнения этого метода
 	 	peredacha.quantity++; 	
	}	

public static void vyvod ()
	{
	// вывод массива
		System.out.println("");
		System.out.println("После сортировки:");
		System.out.println("");
		for(int i=0; i<razmer; i++)
		System.out.println(mass[i]);	
	}
}



