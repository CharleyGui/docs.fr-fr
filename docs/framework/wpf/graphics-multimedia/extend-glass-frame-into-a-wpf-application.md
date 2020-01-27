---
title: Étendre le cadre de transparence dans une application WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
ms.openlocfilehash: b78547aa8b414c585bb2e5c9c6680ed159731bc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746530"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a><span data-ttu-id="5406b-102">Étendre le cadre de transparence dans une application WPF</span><span class="sxs-lookup"><span data-stu-id="5406b-102">Extend Glass Frame Into a WPF Application</span></span>

<span data-ttu-id="5406b-103">Cette rubrique montre comment étendre le cadre de transparence Windows Vista dans la zone cliente d’une application Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="5406b-103">This topic demonstrates how to extend the Windows Vista glass frame into the client area of a Windows Presentation Foundation (WPF) application.</span></span>

> [!NOTE]
> <span data-ttu-id="5406b-104">Cet exemple ne fonctionne que sur un ordinateur Windows Vista exécutant le Gestionnaire de fenêtrage (DWM) avec la vitre activée.</span><span class="sxs-lookup"><span data-stu-id="5406b-104">This example will only work on a Windows Vista machine running the Desktop Window Manager (DWM) with glass enabled.</span></span> <span data-ttu-id="5406b-105">Windows Vista Édition personnelle basique ne prend pas en charge l’effet de transparence transparent.</span><span class="sxs-lookup"><span data-stu-id="5406b-105">Windows Vista Home Basic edition does not support the transparent glass effect.</span></span> <span data-ttu-id="5406b-106">Les zones qui s’affichent normalement avec l’effet de transparence sur les autres éditions de Windows Vista sont rendues opaques.</span><span class="sxs-lookup"><span data-stu-id="5406b-106">Areas that would typically render with the transparent glass effect on other editions of Windows Vista are rendered opaque.</span></span>

## <a name="example"></a><span data-ttu-id="5406b-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="5406b-107">Example</span></span>

<span data-ttu-id="5406b-108">L’illustration suivante montre le cadre de transparence étendu dans la barre d’adresses d’Internet Explorer 7 :</span><span class="sxs-lookup"><span data-stu-id="5406b-108">The following image illustrates the glass frame extended into the address bar of Internet Explorer 7:</span></span>

![Capture d’écran montrant le cadre de transparence étendu en arrière-plan de la barre d’adresses IE7.](./media/extend-glass-frame-into-a-wpf-application/internet-explorer-glass-frame-extended-address-bar.png)

<span data-ttu-id="5406b-110">Pour étendre le cadre de transparence sur une application WPF, l’accès à l’API non managée est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5406b-110">To extend the glass frame on a WPF application, access to unmanaged API is needed.</span></span> <span data-ttu-id="5406b-111">L’exemple de code suivant effectue un appel de code non managé (PInvoke) pour les deux API nécessaires à l’extension du frame dans la zone cliente.</span><span class="sxs-lookup"><span data-stu-id="5406b-111">The following code example does a Platform Invoke (pinvoke) for the two API needed to extend the frame into the client area.</span></span> <span data-ttu-id="5406b-112">Chacune de ces API est déclarée dans une classe appelée **NonClientRegionAPI**.</span><span class="sxs-lookup"><span data-stu-id="5406b-112">Each of these API are declared in a class called **NonClientRegionAPI**.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential)]
public struct MARGINS
{
    public int cxLeftWidth;      // width of left border that retains its size
    public int cxRightWidth;     // width of right border that retains its size
    public int cyTopHeight;      // height of top border that retains its size
    public int cyBottomHeight;   // height of bottom border that retains its size
};

[DllImport("DwmApi.dll")]
public static extern int DwmExtendFrameIntoClientArea(
    IntPtr hwnd,
    ref MARGINS pMarInset);
```

```vb
<StructLayout(LayoutKind.Sequential)>
Public Structure MARGINS
    Public cxLeftWidth As Integer ' width of left border that retains its size
    Public cxRightWidth As Integer ' width of right border that retains its size
    Public cyTopHeight As Integer ' height of top border that retains its size
    Public cyBottomHeight As Integer ' height of bottom border that retains its size
End Structure

<DllImport("DwmApi.dll")>
Public Shared Function DwmExtendFrameIntoClientArea(ByVal hwnd As IntPtr, ByRef pMarInset As MARGINS) As Integer
End Function
```

<span data-ttu-id="5406b-113">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) est la fonction DWM qui étend le cadre dans la zone cliente.</span><span class="sxs-lookup"><span data-stu-id="5406b-113">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) is the DWM function that extends the frame into the client area.</span></span> <span data-ttu-id="5406b-114">Elle nécessite deux paramètres ; un handle de fenêtre et une structure [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins).</span><span class="sxs-lookup"><span data-stu-id="5406b-114">It takes two parameters; a window handle and a [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) structure.</span></span> <span data-ttu-id="5406b-115">[MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) indique à DWM le niveau d’extension du cadre dans la zone cliente.</span><span class="sxs-lookup"><span data-stu-id="5406b-115">[MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) is used to tell the DWM how much extra the frame should be extended into the client area.</span></span>

## <a name="example"></a><span data-ttu-id="5406b-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="5406b-116">Example</span></span>

<span data-ttu-id="5406b-117">Pour utiliser la fonction [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea), un handle de fenêtre doit être obtenu.</span><span class="sxs-lookup"><span data-stu-id="5406b-117">To use the [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) function, a window handle must be obtained.</span></span> <span data-ttu-id="5406b-118">Dans WPF, le handle de fenêtre peut être obtenu à partir de la propriété <xref:System.Windows.Interop.HwndSource.Handle%2A> d’un <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="5406b-118">In WPF, the window handle can be obtained from the <xref:System.Windows.Interop.HwndSource.Handle%2A> property of an <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="5406b-119">Dans l’exemple suivant, le frame est étendu dans la zone cliente de l’événement <xref:System.Windows.FrameworkElement.Loaded> de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="5406b-119">In the following example, the frame is extended into the client area on the <xref:System.Windows.FrameworkElement.Loaded> event of the window.</span></span>

```csharp
void OnLoaded(object sender, RoutedEventArgs e)
{
   try
   {
      // Obtain the window handle for WPF application
      IntPtr mainWindowPtr = new WindowInteropHelper(this).Handle;
      HwndSource mainWindowSrc = HwndSource.FromHwnd(mainWindowPtr);
      mainWindowSrc.CompositionTarget.BackgroundColor = Color.FromArgb(0, 0, 0, 0);

      // Get System Dpi
      System.Drawing.Graphics desktop = System.Drawing.Graphics.FromHwnd(mainWindowPtr);
      float DesktopDpiX = desktop.DpiX;
      float DesktopDpiY = desktop.DpiY;

      // Set Margins
      NonClientRegionAPI.MARGINS margins = new NonClientRegionAPI.MARGINS();

      // Extend glass frame into client area
      // Note that the default desktop Dpi is 96dpi. The  margins are
      // adjusted for the system Dpi.
      margins.cxLeftWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cxRightWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cyTopHeight = Convert.ToInt32(((int)topBar.ActualHeight + 5) * (DesktopDpiX / 96));
      margins.cyBottomHeight = Convert.ToInt32(5 * (DesktopDpiX / 96));

      int hr = NonClientRegionAPI.DwmExtendFrameIntoClientArea(mainWindowSrc.Handle, ref margins);
      //
      if (hr < 0)
      {
         //DwmExtendFrameIntoClientArea Failed
      }
   }
   // If not Vista, paint background white.
   catch (DllNotFoundException)
   {
      Application.Current.MainWindow.Background = Brushes.White;
   }
}
```

## <a name="example"></a><span data-ttu-id="5406b-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="5406b-120">Example</span></span>

<span data-ttu-id="5406b-121">L’exemple suivant montre une simple fenêtre dans laquelle le cadre est étendu dans la zone cliente.</span><span class="sxs-lookup"><span data-stu-id="5406b-121">The following example shows a simple window in which the frame is extended into the client area.</span></span> <span data-ttu-id="5406b-122">Le cadre est étendu derrière la bordure supérieure qui contient les deux objets <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="5406b-122">The frame is extended behind the top border that contains the two <xref:System.Windows.Controls.TextBox> objects.</span></span>

```xaml
<Window x:Class="SDKSample.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Extended Glass in WPF" Height="300" Width="400"
    Loaded="OnLoaded" Background="Transparent"
    >
  <Grid ShowGridLines="True">
    <DockPanel Name="mainDock">
      <!-- The border is used to compute the rendered height with margins.
           topBar contents will be displayed on the extended glass frame.-->
      <Border Name="topBar" DockPanel.Dock="Top" >
        <Grid Name="grid">
          <Grid.ColumnDefinitions>
            <ColumnDefinition MinWidth="100" Width="*"/>
            <ColumnDefinition Width="Auto"/>
          </Grid.ColumnDefinitions>
          <TextBox Grid.Column="0" MinWidth="100" Margin="0,0,10,5">Path</TextBox>
          <TextBox Grid.Column="1" MinWidth="75" Margin="0,0,0,5">Search</TextBox>
        </Grid>
      </Border>
      <Grid DockPanel.Dock="Top" >
        <Grid.ColumnDefinitions>
          <ColumnDefinition/>
        </Grid.ColumnDefinitions>
        <TextBox Grid.Column="0" AcceptsReturn="True"/>
      </Grid>
    </DockPanel>
  </Grid>
</Window>
```

<span data-ttu-id="5406b-123">L’illustration suivante montre le cadre de transparence étendu dans une application WPF :</span><span class="sxs-lookup"><span data-stu-id="5406b-123">The following image illustrates the glass frame extended into a WPF application:</span></span>

![Capture d’écran montrant un cadre de transparence étendu dans une application WPF.](./media/extend-glass-frame-into-a-wpf-application/glass-frame-extended-wpf-application.png)

## <a name="see-also"></a><span data-ttu-id="5406b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5406b-125">See also</span></span>

- [<span data-ttu-id="5406b-126">Présentation de Gestionnaire de fenêtrage</span><span class="sxs-lookup"><span data-stu-id="5406b-126">Desktop Window Manager Overview</span></span>](/windows/desktop/dwm/dwm-overview)
- [<span data-ttu-id="5406b-127">Gestionnaire de fenêtrage vue d’ensemble du flou</span><span class="sxs-lookup"><span data-stu-id="5406b-127">Desktop Window Manager Blur Overview</span></span>](/windows/desktop/dwm/blur-ovw)
- [<span data-ttu-id="5406b-128">DwmExtendFrameIntoClientArea</span><span class="sxs-lookup"><span data-stu-id="5406b-128">DwmExtendFrameIntoClientArea</span></span>](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
