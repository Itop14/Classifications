# Classifications C#

This is a simple classification system that asks a series of Yes/No questions in order to work out what type of animal is being looked at 


    using System;
    using System.Collections.Generic;
    using System.ComponentModel;
    using System.Data;
    using System.Drawing;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Windows.Forms;
    
    namespace Classifications
    {
        public partial class Form1 : Form
        {
            private readonly string[] tree = {
                null, // Index 0 (not used)
                "QIs it a mammal",
                "QIs it a domestic pet",
                "QDoes it live in water",
                "Adog",
                "Acat",
                "Afish",
                "Abird"
            };
    
            private int current = 1;
    
            public Form1()
            {
                InitializeComponent();
                ShowQuestion();
                R_btn.Hide();
            }
    
            private void ShowQuestion()
            {
                if (tree[current].StartsWith("Q"))
                {
                    label1.Text = tree[current].Substring(1) + "?";
                }
                else
                {
                    label1.Text = "My guess would be... " + tree[current].Substring(1);
                    Yesbtn.Enabled = false;
                    Nobtn.Enabled = false;
                    R_btn.Show();
                }
            }
    
            private void Yesbtn_Click(object sender, EventArgs e)
            {
                current = current * 2; //moves to the left child
                ShowQuestion();
            }
    
            private void Nobtn_Click(object sender, EventArgs e)
            {
                current = current * 2 + 1;//moves to the right child
                ShowQuestion();
            }
    
            private void R_btn_Click(object sender, EventArgs e)
            {
                current = 1;
                ShowQuestion();
                Yesbtn.Enabled = true;
                Nobtn.Enabled = true;
                R_btn.Hide();
            }
        }
    }
