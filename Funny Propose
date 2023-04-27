#include <windows.h>

LRESULT CALLBACK WndProc(HWND hwnd, UINT msg, WPARAM wParam, LPARAM lParam);

int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int nCmdShow)
{
    HWND hwnd;
    MSG msg;
    WNDCLASS wc = {0};

    wc.lpfnWndProc   = WndProc;
    wc.hInstance     = hInstance;
    wc.hbrBackground = (HBRUSH)(COLOR_WINDOW+1);
    wc.lpszClassName = "Marriage Proposal";

    if(!RegisterClass(&wc))
        return -1;

    hwnd = CreateWindow(
        "Marriage Proposal",
        "Will You Marry Me?",
        WS_OVERLAPPED | WS_CAPTION | WS_SYSMENU,
        CW_USEDEFAULT, CW_USEDEFAULT, 240, 120,
        NULL, NULL, hInstance, NULL);

    ShowWindow(hwnd, nCmdShow);

    while(GetMessage(&msg, NULL, 0, 0))
    {
        TranslateMessage(&msg);
        DispatchMessage(&msg);
    }

    return msg.wParam;
}

LRESULT CALLBACK WndProc(HWND hwnd, UINT msg, WPARAM wParam, LPARAM lParam)
{
    static int counter = 0;
    switch(msg)
    {
        case WM_COMMAND:
            switch(LOWORD(wParam))
            {
                case IDYES:
                    MessageBox(hwnd, "Thank you for accepting!", "Proposal", MB_OK | MB_ICONINFORMATION);
                    DestroyWindow(hwnd);
                    break;
                case IDNO:
                    if(counter < 100)
                    {
                        int answer = MessageBox(hwnd, "Are you sure?", "Proposal", MB_YESNO | MB_ICONQUESTION);
                        if(answer == IDYES)
                        {
                            MessageBox(hwnd, "Maybe next time.", "Proposal", MB_OK | MB_ICONINFORMATION);
                            DestroyWindow(hwnd);
                        }
                        else if(answer == IDNO)
                        {
                            counter++;
                        }
                    }
                    else
                    {
                        MessageBox(hwnd, "Fuck You!", "Proposal", MB_OK | MB_ICONERROR);
                        DestroyWindow(hwnd);
                    }
                    break;
            }
            break;
        case WM_DESTROY:
            PostQuitMessage(0);
            break;
        default:
            return DefWindowProc(hwnd, msg, wParam, lParam);
    }

    return 0;
}
