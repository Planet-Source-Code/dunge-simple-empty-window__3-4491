<div align="center">

## Simple Empty Window


</div>

### Description

Create an empty window with the less code possible.
 
### More Info
 
I just wanted to submit this code because I remember when I first started w32 programming the only thing I could find here was a bug windows with lot of controls and useless code.. so here it is the smallest ay I found to create a working windows in VC++


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Dunge](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/dunge.md)
**Level**          |Beginner
**User Rating**    |3.7 (11 globes from 3 users)
**Compatibility**  |Microsoft Visual C\+\+
**Category**       |[Controls/ Forms/ Dialogs/ Menus](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/controls-forms-dialogs-menus__3-3.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/dunge-simple-empty-window__3-4491/archive/master.zip)





### Source Code

```
#include <windows.h>
bool done;
HWND test;
LRESULT CALLBACK Proc(HWND hwnd, UINT msg, WPARAM wParam, LPARAM lParam)
{
	if (msg == WM_DESTROY)
	{
		PostQuitMessage(0);
		done = true;
	}
	return (DefWindowProc(hwnd, msg, wParam, lParam));
}
int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int nCmdShow)
{
	WNDCLASSEX wc;
	MSG msg;
	wc.cbSize = sizeof(WNDCLASSEX);
	wc.style = CS_HREDRAW | CS_VREDRAW;
	wc.lpfnWndProc = (WNDPROC)Proc;
	wc.cbClsExtra = 0;
	wc.cbWndExtra = 0;
	wc.hInstance = hInstance;
	wc.hIcon = LoadIcon(NULL, IDI_APPLICATION);
	wc.hCursor = LoadCursor(NULL,IDC_ARROW);
	wc.hbrBackground = (HBRUSH)(COLOR_APPWORKSPACE);
	wc.lpszClassName = "LaClass";
	wc.lpszMenuName = 0;
	RegisterClassEx(&wc);
	test = CreateWindowEx(NULL, "LaClass", "Our First Window", WS_VISIBLE | WS_OVERLAPPEDWINDOW, CW_USEDEFAULT, CW_USEDEFAULT, CW_USEDEFAULT, CW_USEDEFAULT, NULL, NULL, hInstance, NULL);
	while(!done)
	{
		if (GetMessage(&msg,0,0,0))
		{
			TranslateMessage(&msg);
			DispatchMessage(&msg);
		}
	}
	return WPARAM(msg.wParam);
}
```

