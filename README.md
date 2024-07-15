using System.Drawing;

namespace Pikachu

{

    class Program

    {

        static void Main(string[] args)

        {

            // Tạo đối tượng Graphics

            Graphics gr = Graphics.FromHwnd(this.Handle);

            // Vẽ bảng điện tử

            Rectangle board = new Rectangle(0, 0, 500, 500);

            gr.FillRectangle(Brushes.White, board);

            // Vẽ các ô điện tử

            for (int i = 0; i < 10; i++)

            {

                for (int j = 0; j < 10; j++)

                {

                    // Tạo đối tượng Rectangle cho ô điện tử

                    Rectangle cell = new Rectangle(i * 50, j * 50, 50, 50);

                    // Xác định màu của ô điện tử

                    Color color = Color.FromArgb(Random.Next(255), Random.Next(255), Random.Next(255));

                    // Vẽ ô điện tử

                    gr.FillRectangle(Brushes.Yellow, cell);

                    gr.FillRectangle(Brushes.Black, cell, new Rectangle(1, 1, 48, 48));

                }

            }

            // Vẽ Pikachu

            Rectangle pikachu = new Rectangle(250, 250, 50, 50);

            gr.FillRectangle(Brushes.Yellow, pikachu);

            gr.FillRectangle(Brushes.Black, pikachu, new Rectangle(1, 1, 48, 48));

            // Vẽ game loop

            while (true)

            {

                // Xử lý các sự kiện

                ProcessEvents();

                // Di chuyển Pikachu

                MovePikachu();

                // Kiểm tra xem người chơi có thắng game hay không

                if (IsWin())

                {

                    // Xuất thông báo người chơi thắng game

                    MessageBox.Show(“Bạn đã thắng!”);

                    break;

                }

 

                // Vẽ lại giao diện người dùng

                gr.Clear(Color.White);

                DrawBoard(gr);

                DrawCells(gr);

                DrawPikachu(gr);

            }

        }
