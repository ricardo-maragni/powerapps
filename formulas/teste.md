# 📄 Nome do snippet — Envio de e-mail de aprovação

## 🧠 Descrição
Envia um e-mail automático para o aprovador principal após o envio do formulário, tratando erros com `IfError` e notificações visuais no app.

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
