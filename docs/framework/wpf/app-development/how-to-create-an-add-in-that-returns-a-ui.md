---
title: 'Procédure : Créer un complément qui retourne une interface utilisateur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: 1886703e089ed538f68a7221906d815a8ae72076
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182669"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Procédure : Créer un complément qui retourne une interface utilisateur
Cet exemple montre comment créer un complément qui retourne une Windows Presentation Foundation (WPF) à une application hôte autonome WPF.  
  
 Le complément retourne une interface utilisateur qui est un contrôle utilisateur WPF. Le contenu du contrôle utilisateur est un bouton unique qui, quand on clique dessus, affiche une boîte de message. L’application autonome WPF héberge le complément et affiche le contrôle utilisateur (retourné par le complément) en tant que contenu de la fenêtre principale de l’application.  
  
 **Composants requis**  
  
 Cet exemple met en surbrillance les extensions WPF du modèle de complément .NET Framework qui active ce scénario et suppose ce qui suit :  
  
- Connaissance du modèle de complément .NET Framework, y compris le pipeline, le complément et le développement d’hôtes. Si vous n’êtes pas familiarisé avec ces concepts, consultez [compléments et extensibilité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Pour obtenir un didacticiel qui illustre l’implémentation d’un pipeline, d’un complément et d’une application hôte, [consultez Procédure pas à pas : Création d’une application](../../add-ins/walkthrough-create-extensible-app.md)extensible.  
  
- Connaissance des extensions WPF du modèle de complément .NET Framework, qui se trouve ici : [Vue d’ensemble des compléments WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Exemple  
 La création d’un complément qui retourne une interface utilisateur WPF nécessite du code spécifique pour chaque segment de pipeline, le complément et l’application hôte.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implémentation du segment de pipeline de contrat  
 Une méthode doit être définie par le contrat pour retourner une interface utilisateur, et sa valeur de retour doit être <xref:System.AddIn.Contract.INativeHandleContract>de type. Cela est démontré par la `GetAddInUI` méthode `IWPFAddInContract` du contrat dans le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implémentation du segment de pipeline de vue de complément  
 Étant donné que le complément implémente le [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] fourni en tant que sous-classes <xref:System.Windows.FrameworkElement>de, la méthode sur la vue de complément qui correspond à `IWPFAddInView.GetAddInUI` doit retourner une valeur de type <xref:System.Windows.FrameworkElement>. Le code suivant illustre la vue de complément du contrat, implémentée en tant qu’interface.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implémentation du segment de pipeline d’adaptateur côté complément  
 La méthode de contrat retourne <xref:System.AddIn.Contract.INativeHandleContract>un, mais le complément retourne un <xref:System.Windows.FrameworkElement> (comme spécifié par la vue de complément). Par conséquent, <xref:System.Windows.FrameworkElement> doit être converti en un <xref:System.AddIn.Contract.INativeHandleContract> avant de traverser la limite d’isolation. Ce travail est effectué par l’adaptateur côté complément en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, comme illustré dans le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implémentation du segment de pipeline de vue hôte  
 Étant donné que l’application hôte affiche <xref:System.Windows.FrameworkElement>un, la méthode sur la vue hôte qui correspond à `IWPFAddInHostView.GetAddInUI` doit retourner une valeur de type <xref:System.Windows.FrameworkElement>. Le code suivant illustre la vue hôte du contrat, implémentée en tant qu’interface.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implémentation du segment de pipeline d’adaptateur côté hôte  
 La méthode de contrat retourne <xref:System.AddIn.Contract.INativeHandleContract>un, mais l’application hôte attend un <xref:System.Windows.FrameworkElement> (comme spécifié par la vue hôte). Par conséquent, <xref:System.AddIn.Contract.INativeHandleContract> doit être converti en un <xref:System.Windows.FrameworkElement> après avoir franchi la limite d’isolation. Ce travail est effectué par l’adaptateur côté hôte en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, comme illustré dans le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implémentation du complément  
 Une fois l’adaptateur côté complément et la vue de complément créés, le complément`WPFAddIn1.AddIn`() doit implémenter la `IWPFAddInView.GetAddInUI` méthode pour <xref:System.Windows.Controls.UserControl> retourner un <xref:System.Windows.FrameworkElement> objet (dans cet exemple). L’implémentation de <xref:System.Windows.Controls.UserControl>, `AddInUI`, est indiquée par le code suivant.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 L’implémentation de `IWPFAddInView.GetAddInUI` par le complément doit simplement retourner une nouvelle instance de `AddInUI`, comme le montre le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Implémentation de l'application hôte.  
 L’adaptateur côté hôte et la vue hôte étant créés, l’application hôte peut utiliser le modèle de complément .NET Framework pour ouvrir le pipeline, acquérir une vue hôte du complément et appeler la `IWPFAddInHostView.GetAddInUI` méthode. Ces étapes sont présentées dans le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Voir aussi

- [Compléments et extensibilité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Vue d’ensemble des compléments WPF](wpf-add-ins-overview.md)
