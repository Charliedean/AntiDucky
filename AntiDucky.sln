using System;
using System.Management;
using System.Windows.Forms;
using System.Runtime.InteropServices;



namespace WMISample
{
    
    public class MyWMIQuery
    {
        [DllImport("user32")]
        public static extern void LockWorkStation();
        public static void Main()
        {
            try
            {
                ManagementObjectSearcher searcher =
                    new ManagementObjectSearcher("root\\CIMV2",
                    "SELECT * FROM Win32_Keyboard");
                int kb = 0;
                bool alex = false;
                while (true)
                {
                    int num = 0;
                    System.Threading.Thread.Sleep(100);
                    foreach (ManagementObject queryObj in searcher.Get())
                    {
                        num += 1;
                    }
                    if (!alex)
                    {
                        kb = num;
                        alex = true;
                    }
                    
                    if (num > kb)
                    {
                        LockWorkStation();
                    }
                }
            }
            catch (ManagementException e)
            {
                MessageBox.Show("An error occurred while querying for WMI data: " + e.Message);
            }
        }
    }
}
