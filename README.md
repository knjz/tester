tester
======
first test project for the many PC


pull = download
push = upload



using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace wfPassGen
{
    public partial class Form_general : Form
    {
        public Form_general()
        {
            InitializeComponent();
        }

        private void btn_copyClipboard_Click(object sender, EventArgs e)
        {
            Clipboard.SetText(textBox_outputPass.Text);
        }

        private void btn_Generate_Click(object sender, EventArgs e)
        {
            GenPass((int)numericCountPass.Value);
        }

        private void GenPass(int countPass)
        {
            var random = new Random();
            string password = null;

            var Alphabet = new List<char> {'a','b','c','d','e','f','g','h','i','j',
                'k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z'};
            var AlphabetUP = new List<char> {'A','B','C','D','E','F','G','H','I','J',
                'K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z'};
            var Numeric = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
            //var specTM = new List<char> { '/', '*', '-', '+', '=', '_', '%', '@', '!', '?' };

            if (countPass != 0)
            {


                for (int i = 0; i < countPass; i++)
                {
                    if (random.Next(0, 4) == 0)
                        password += Alphabet[random.Next(0, 26)].ToString();
                    else if (random.Next(0, 4) == 1)
                        password += AlphabetUP[random.Next(0, 26)].ToString();
                    else
                        password += Numeric[random.Next(0, 10)].ToString();
                }

                textBox_outputPass.ForeColor = Color.Black;
                textBox_outputPass.Text = password;
            }
            else
            {
                MessageBox.Show("Incorect count password");
            }
        }
    }
}
