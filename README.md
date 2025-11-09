using System;
using System.Collections.Generic;
using System.Threading;

namespace TaskSchedulerApp
{
    class TaskItem
    {
        public string Name { get; set; }
        public int Delay { get; set; }
    }

    class Program
    {
        static void Main()
        {
            List<TaskItem> tasks = new List<TaskItem>();

            while (true)
            {
                Console.WriteLine("\n1. Add Task\n2. Run Tasks\n3. Exit");
                Console.Write("Choose: ");
                int choice = int.Parse(Console.ReadLine());

                if (choice == 1)
                {
                    Console.Write("Enter task name: ");
                    string name = Console.ReadLine();
                    Console.Write("Enter delay (seconds): ");
                    int delay = int.Parse(Console.ReadLine());
                    tasks.Add(new TaskItem { Name = name, Delay = delay });
                }
                else if (choice == 2)
                {
                    foreach (var t in tasks)
                    {
                        Console.WriteLine($"Executing {t.Name} after {t.Delay}s...");
                        Thread.Sleep(t.Delay * 1000);
                        Console.WriteLine($"Task '{t.Name}' done!");
                    }
                }
                else break;
            }
        }
    }
}
