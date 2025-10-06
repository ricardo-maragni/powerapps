# 🚀 Barra de progresso

## 🧠 Descrição
Você pode utilizar para medir o progresso de determinados contextos dentro do aplicativo.

## 💻 Código Power Fx
```powerfx
IfError(
    SubmitForm(Form1);
    Notify("Erro ao enviar", NotificationType.Error);
    Office365Outlook.SendEmailV2(
        emails_lbl_1.Text;
        "Aprovação necessária";
        "Por favor, revise a solicitação: " & Form1.Last.SubmissionId
    )
)


//Barra de progresso simples
"<progress value='75' max='100'></progress>"

//Barra de progresso com largura e autura definidas
"<progress value='75' max='100' style='width:100%;height:10px'></progress>"

//Com legenda
" 
<div style='position: relative; width: 100%; height: 80px;'> 
<progress value='60' max='100' style='width: 100%; height: 100%; accent-color:blue'></progress> 
<span style=' position: absolute; top: 0; left: 0; width: 100%; height: 100%; display: flex; align-items: center; justify-content: center; font-size: 20px; font-weight: bold; color: white; '> 60% </span> </div>
"
