---
title: 'Procédure pas à pas : hébergement d’un contrôle Win32 dans WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: cc27189afd2185d5f0a1eeacccf4c537dd3d9c2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917543"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>Procédure pas à pas : hébergement d’un contrôle Win32 dans WPF
Windows Presentation Foundation (WPF) fournit un environnement riche pour la création d’applications. Toutefois, lorsque vous avez un investissement important dans du code Win32, il peut être plus efficace de réutiliser au moins une partie de ce code dans votre application WPF au lieu de le réécrire complètement. WPF fournit un mécanisme simple pour héberger une fenêtre Win32, sur une page WPF.  
  
 Cette rubrique vous guide à travers une application, qui [héberge un contrôle ListBox Win32 dans WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), qui héberge un contrôle de zone de liste Win32. Cette procédure générale peut être étendue à l’hébergement d’une fenêtre Win32.  

<a name="requirements"></a>   
## <a name="requirements"></a>Configuration requise  
 Cette rubrique suppose une connaissance de base de la programmation des API WPF et Windows. Pour une présentation de base de la programmation WPF, consultez [prise en main](../getting-started/index.md). Pour une introduction à la programmation des API Windows, consultez l’un des nombreux ouvrages sur le sujet, en particulier *Programming Windows* de Charles Petzold.  
  
 Étant donné que l’exemple qui accompagne cette rubrique est implémenté C#dans, il utilise les services d’appel de code non managé (PInvoke) pour accéder à l’API Windows. Une certaine connaissance de PInvoke est utile, mais pas essentielle.  
  
> [!NOTE]
> Cette rubrique comprend plusieurs exemples de code tirés de l'exemple associé. Cependant, pour une meilleure lecture, il n'inclut pas la totalité de l'exemple de code. Vous pouvez obtenir ou afficher le code complet à partir de [l’hébergement d’un contrôle ListBox Win32 dans WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Procédure de base  
 Cette section décrit la procédure de base pour l’hébergement d’une fenêtre Win32 sur une page WPF. Les sections restantes décrivent chaque étape en détails.  
  
 La procédure d’hébergement de base est la suivante :  
  
1. Implémentez une page WPF pour héberger la fenêtre. L’une des techniques consiste à <xref:System.Windows.Controls.Border> créer un élément pour réserver une section de la page pour la fenêtre hébergée.  
  
2. Implémentez une classe pour héberger le contrôle qui hérite de <xref:System.Windows.Interop.HwndHost>.  
  
3. Dans cette classe, substituez le <xref:System.Windows.Interop.HwndHost> membre <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>de classe.  
  
4. Créez la fenêtre hébergée en tant qu’enfant de la fenêtre qui contient la page WPF. Bien que la programmation WPF conventionnelle n’ait pas besoin de l’utiliser explicitement, la page d’hébergement est une fenêtre avec un handle (HWND). Vous recevez la page HWND par le `hwndParent` biais du paramètre <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> de la méthode. La fenêtre hébergée doit être créée comme un enfant de ce HWND.  
  
5. Une fois que vous avez créé la fenêtre hôte, retournez le HWND de la fenêtre hébergée. Si vous souhaitez héberger un ou plusieurs contrôles Win32, vous créez généralement une fenêtre hôte en tant qu’enfant du HWND et définissez les enfants des contrôles de cette fenêtre hôte. L’encapsulation des contrôles dans une fenêtre hôte offre un moyen simple pour votre page WPF de recevoir des notifications des contrôles, ce qui gère certains problèmes Win32 particuliers avec les notifications à travers la limite HWND.  
  
6. Gérez les messages sélectionnés envoyés à la fenêtre hôte, comme les notifications des contrôles enfants. Il existe deux manières de procéder.  
  
    - Si vous préférez gérer des messages dans votre classe d’hébergement, substituez <xref:System.Windows.Interop.HwndHost.WndProc%2A> la méthode de <xref:System.Windows.Interop.HwndHost> la classe.  
  
    - Si vous préférez que WPF gère les messages, gérez l' <xref:System.Windows.Interop.HwndHost> événement de classe <xref:System.Windows.Interop.HwndHost.MessageHook> dans votre code-behind. Cet événement se produit pour chaque message reçu par la fenêtre hébergée. Si vous choisissez cette option, vous devez toujours remplacer <xref:System.Windows.Interop.HwndHost.WndProc%2A>, mais vous n’avez besoin que d’une implémentation minimale.  
  
7. Substituez les <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> méthodes <xref:System.Windows.Interop.HwndHost.WndProc%2A> et de <xref:System.Windows.Interop.HwndHost>. Vous devez substituer ces méthodes pour satisfaire le <xref:System.Windows.Interop.HwndHost> contrat, mais vous devrez peut-être uniquement fournir une implémentation minimale.  
  
8. Dans votre fichier code-behind, créez une instance de la classe d’hébergement du contrôle et définissez-la comme <xref:System.Windows.Controls.Border> un enfant de l’élément destiné à héberger la fenêtre.  
  
9. Communiquez avec la fenêtre hébergée en [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] lui envoyant des messages et en gérant les messages de ses fenêtres enfants, telles que les notifications envoyées par les contrôles.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Implémenter la disposition de la page  
 La disposition de la page WPF qui héberge le contrôle ListBox se compose de deux régions. Le côté gauche de la page héberge plusieurs contrôles WPF qui fournissent un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] qui vous permet de manipuler le contrôle Win32. Le coin en haut à droite de la page contient une zone carrée pour le contrôle ListBox hébergé.  
  
 Le code permettant d’implémenter cette disposition est assez simple. L’élément racine est un <xref:System.Windows.Controls.DockPanel> qui a deux éléments enfants. Le premier est un <xref:System.Windows.Controls.Border> élément qui héberge le contrôle ListBox. Il occupe un carré de 200 x 200 en haut à droite de la page. Le deuxième est un <xref:System.Windows.Controls.StackPanel> élément qui contient un jeu de contrôles WPF qui affichent des informations et vous permettent de manipuler le contrôle ListBox en définissant les propriétés d’interopérabilité exposées. Pour chacun des éléments qui sont des enfants de <xref:System.Windows.Controls.StackPanel>, consultez le document de référence pour les différents éléments utilisés pour plus d’informations sur ce que ces éléments sont ou ce qu’ils font, ceux-ci sont répertoriés dans l’exemple de code ci-dessous, mais ils ne seront pas expliqués ici (de base le modèle d’interopérabilité ne requiert pas l’un d’eux, ils sont fournis pour ajouter de l’interactivité à l’exemple).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implémenter une classe pour héberger le contrôle Microsoft Win32  
 Le cœur de cet exemple est la classe qui héberge réellement le contrôle, ControlHost.cs. Hérite de <xref:System.Windows.Interop.HwndHost>. Le constructeur prend deux paramètres, Height et Width, qui correspondent à la hauteur et à la largeur <xref:System.Windows.Controls.Border> de l’élément qui héberge le contrôle ListBox. Ces valeurs sont utilisées ultérieurement pour s’assurer que la taille du contrôle correspond à <xref:System.Windows.Controls.Border> l’élément.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Il existe également un ensemble de constantes. Ces constantes sont largement tirées de winuser. h et vous permettent d’utiliser des noms conventionnels lors de l’appel de fonctions Win32.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Substituer BuildWindowCore pour créer la fenêtre Microsoft Win32  
 Vous substituez cette méthode pour créer la fenêtre Win32 qui sera hébergée par la page et établir la connexion entre la fenêtre et la page. Comme cet exemple implique l’hébergement d’un contrôle ListBox, deux fenêtres sont créées. La première est la fenêtre qui est réellement hébergée par la page WPF. Le contrôle ListBox est créé comme un enfant de cette fenêtre.  
  
 Cette approche a pour but de simplifier le processus de réception des notifications du contrôle. La <xref:System.Windows.Interop.HwndHost> classe vous permet de traiter les messages envoyés à la fenêtre qu’elle héberge. Si vous hébergez directement un contrôle Win32, vous recevez les messages envoyés à la boucle de message interne du contrôle. Vous pouvez afficher le contrôle et lui envoyer des messages, mais vous ne recevez pas les notifications que le contrôle envoie à sa fenêtre parente. Cela signifie, entre autres, que vous n’avez aucun moyen de détecter quand l’utilisateur interagit avec le contrôle. Au lieu de cela, créez une fenêtre hôte et définissez le contrôle comme un enfant de cette fenêtre. Cela vous permet de traiter les messages de la fenêtre hôte, y compris les notifications que le contrôle lui envoie. Pour des raisons pratiques, comme la fenêtre hôte n’est guère plus qu’un simple wrapper pour le contrôle, le package est un contrôle ListBox.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Créer la fenêtre hôte et un contrôle ListBox  
 Vous pouvez utiliser PInvoke pour créer une fenêtre hôte pour le contrôle en créant et en inscrivant une classe de fenêtre, et ainsi de suite. Toutefois, vous pouvez, beaucoup plus simplement, créer une fenêtre avec la classe de fenêtre « statique » prédéfinie. Cela vous fournit la procédure de fenêtre dont vous avez besoin pour recevoir les notifications du contrôle et nécessite un minimum de codage.  
  
 Le HWND du contrôle est exposé au moyen d’une propriété en lecture seule, de sorte que la page hôte peut l’utiliser pour envoyer des messages au contrôle.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 Le contrôle ListBox est créé comme un enfant de la fenêtre hébergée. La hauteur et la largeur des deux fenêtres sont définies sur les valeurs passées au constructeur, comme décrit ci-dessus. Cela garantit que la taille de la fenêtre hôte et du contrôle est identique à la zone réservée dans la page.  Une fois les fenêtres créées, l’exemple retourne un <xref:System.Runtime.InteropServices.HandleRef> objet qui contient le HWND de la fenêtre hôte.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Implémenter DestroyWindow et WndProc  
 En plus <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>de, vous devez également substituer les <xref:System.Windows.Interop.HwndHost.WndProc%2A> méthodes <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> et de. <xref:System.Windows.Interop.HwndHost> Dans cet exemple, les messages du contrôle sont gérés par le <xref:System.Windows.Interop.HwndHost.MessageHook> gestionnaire, l’implémentation de <xref:System.Windows.Interop.HwndHost.WndProc%2A> et <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> est donc minime. Dans le cas de <xref:System.Windows.Interop.HwndHost.WndProc%2A>, affectez `false` à la valeur `handled` pour indiquer que le message n’a pas été géré et retourne 0. Pour <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, détruisez simplement la fenêtre.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Héberger le contrôle dans la page  
 Pour héberger le contrôle sur la page, vous devez d’abord créer une nouvelle `ControlHost` instance de la classe. Transmettez la hauteur et la largeur de l’élément Border qui contient le`ControlHostElement`contrôle () `ControlHost` au constructeur. Cela garantit que la taille du ListBox est correcte. Vous hébergez ensuite le contrôle sur la page en affectant `ControlHost` l’objet à <xref:System.Windows.Controls.Decorator.Child%2A> la propriété de l' <xref:System.Windows.Controls.Border>hôte.  
  
 L’exemple attache un gestionnaire à l' <xref:System.Windows.Interop.HwndHost.MessageHook> événement `ControlHost` de pour recevoir des messages du contrôle. Cet événement est déclenché pour chaque message envoyé à la fenêtre hébergée. Dans ce cas, il s’agit des messages envoyés à la fenêtre qui encapsule le contrôle ListBox réel, y compris les notifications du contrôle. L’exemple appelle SendMessage pour obtenir des informations du contrôle et modifier son contenu. Les détails sur la façon dont la page communique avec le contrôle sont décrits dans la section suivante.  
  
> [!NOTE]
> Notez qu’il existe deux déclarations PInvoke pour SendMessage. Cela est nécessaire, car l’un `wParam` utilise le paramètre pour passer une chaîne et l’autre l’utilise pour passer un entier. Vous avez besoin d’une déclaration distincte pour chaque signature afin de garantir que les données sont correctement marshalées.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Implémenter une communication entre le contrôle et la page  
 Vous manipulez le contrôle en lui envoyant des messages Windows. Le contrôle vous notifie quand l’utilisateur interagit avec lui en envoyant des notifications à sa fenêtre hôte. L’exemple d' [hébergement d’un contrôle ListBox Win32 dans WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) inclut une interface utilisateur qui fournit plusieurs exemples de fonctionnement:  
  
- Ajouter un élément à la liste.  
  
- Supprimez l'élément sélectionné de la liste.  
  
- Afficher le texte de l'élément actuellement sélectionné.  
  
- Afficher le nombre d’éléments de la liste.  
  
 L’utilisateur peut également sélectionner un élément dans la zone de liste en cliquant dessus, tout comme pour une application Win32 conventionnelle. Les données affichées sont mises à jour chaque fois que l’utilisateur change l’état de la zone de liste en sélectionnant ou ajoutant un élément.  
  
 Pour ajouter des éléments, envoyez un [ `LB_ADDSTRING` message](/windows/desktop/Controls/lb-addstring)à la zone de liste. Pour supprimer des éléments, [`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel) envoyez pour récupérer l’index de la sélection actuelle, [`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring) puis supprimez l’élément. L’exemple envoie [`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)également et utilise la valeur retournée pour mettre à jour l’affichage qui indique le nombre d’éléments. Ces deux instances de [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) utilisent l’une des déclarations PInvoke abordées dans la section précédente.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Lorsque l’utilisateur sélectionne un élément ou modifie sa sélection, le contrôle notifie la fenêtre hôte en lui envoyant un [ `WM_COMMAND` message](/windows/desktop/menurc/wm-command), qui déclenche l' <xref:System.Windows.Interop.HwndHost.MessageHook> événement pour la page. Le gestionnaire reçoit les mêmes informations que la procédure de fenêtre principale de la fenêtre hôte. Il passe également une référence à une valeur booléenne, `handled`. Vous définissez `handled` sur `true` pour indiquer que vous avez géré le message et qu’aucun autre traitement n’est nécessaire.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)est envoyé pour diverses raisons. vous devez donc examiner l’ID de notification pour déterminer s’il s’agit d’un événement que vous souhaitez gérer. L’ID est contenu dans le mot de poids fort `wParam` du paramètre. L’exemple utilise des opérateurs au niveau du bit pour extraire l’ID. Si l’utilisateur a effectué ou modifié sa sélection, l’ID [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange)est.  
  
 Lorsque [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange) est reçu, l’exemple obtient l’index de l’élément sélectionné en envoyant un [ `LB_GETCURSEL` message](/windows/desktop/Controls/lb-getcursel)au contrôle. Pour obtenir le texte, vous devez d’abord <xref:System.Text.StringBuilder>créer un. Vous envoyez ensuite le contrôle à un [ `LB_GETTEXT` message](/windows/desktop/Controls/lb-gettext). Transmettez l' <xref:System.Text.StringBuilder> objet vide `wParam` en tant que paramètre. Lorsque [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) retourne, le <xref:System.Text.StringBuilder> contient le texte de l’élément sélectionné. Cette utilisation de [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) requiert encore une autre déclaration PInvoke.  
  
 Enfin, affectez `true` à la valeur `handled` pour indiquer que le message a été géré.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.HwndHost>
- [Interopérabilité WPF et Win32](wpf-and-win32-interoperation.md)
- [Procédure pas à pas : Ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
