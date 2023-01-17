
function get-apptoken()
{
$Url = "https://login.microsoftonline.com/$TenantName/oauth2/v2.0/token"


    [string]$LoginUrl = "https://login.microsoft.com"  # Graph API URLs.
    [string]$ResourceUrl = "https://graph.microsoft.com"  # Ressource API URLs.
    [string]$AppID = "600ddc79-6d4d-40f2-91f1-12345567889" # App ID aus dem Azure Portal .
    [string]$Appkey = "CGBVJ1C[A?.sil:HeW9qrK27[nsY-oZU" # App Key from Portal
    [string]$TenantName = "mccloud.onmicrosoft.com" #  tenant name.

# Get OAUTH Token
$Body = @{ grant_type = "client_credentials"; 
            resource = $ResourceUrl;
            client_id = $AppID; 
            client_secret = $AppKey 
        }
[object]$OAuth = Invoke-RestMethod -Method Post -Uri "$($LoginUrl)/$($TenantName)/oauth2/token?api-version=1.0" -Body $Body


if ($null -eq $OAuth.access_token) {
    Write-Error "No Access Token"
}
else  {  # Perform REST call.
    $HeaderParams = @{ 
    'Content-Type'='application/json'
    'Authorization' = "$($OAuth.token_type) $($OAuth.access_token)"
    'ExpiresOn'=$OAuth.Expires_on
    }
}
return $HeaderParams
}
