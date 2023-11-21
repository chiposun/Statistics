using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Security.Cryptography;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace Statistics24Hristo
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void label1_Click(object sender, EventArgs e)
        {
           
        }

        private void label1_Click_1(object sender, EventArgs e)
        {

        }

        private void btnAvg_Click(object sender, EventArgs e)
        {
            //Средно ариметрично
            List<int> list = txtNumbers.Text.Split(' ').Select(l => int.Parse(l)).ToList();

            //Average
            var avg = list.Average();

            lblAvg.Text = ("Avarage: " + avg);


            //Median
            list.Sort();
            double median = 0;
            if (list.Count % 2 == 1)
            {
                median = list[(list.Count - 1) / 2];
            }
            else
            {
                var index = list.Count / 2;
                median = (list[index] + list[index - 1]) / 2;
            }
            lblMedi.Text = ("Median: " + median.ToString());

            //Mode
            var mode = list.GroupBy(x => x).OrderByDescending(x => x.Count()).ThenBy(x => x.Key).Select(x => (int)x.Key).FirstOrDefault();


            lblMode.Text = "Mode: " + string.Join(" ", mode);

            //chart
            List<double> ListNums = txtNumbers.Text.Split(' ').Select(double.Parse).ToList();
            chart2.Series["Series1"].Points.Clear();

            foreach (var value in ListNums)
            {
                chart2.Series["Series1"].Points.AddY(value);
            }

        }

        private void chart2_Click(object sender, EventArgs e)
        {

        }

        private void label2_Click(object sender, EventArgs e)
        {

        }

        private void label4_Click(object sender, EventArgs e)
        {

        }

        private void Form1_Load(object sender, EventArgs e)
        {

        }
    }
}
