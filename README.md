local TextChatService = game:GetService('TextChatService')
function Message(Text)
    if not game:GetService("ReplicatedStorage"):FindFirstChild('DefaultChatSystemChatEvents') then
        game:GetService("TextChatService").TextChannels.RBXGeneral:SendAsync(Text)
    else
        game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(Text, 'All')
    end
end
local Request = http_request or request or HttpPost or syn.request
local Response = Request({
    Url = _G.URLSTRING,
    Method = "GET"
})
linec = 1
for line in string.gmatch(Response.Body, '([^\n]+)') do
    print("["..tostring(linec).."] "..line)
    if _G.SHOWLINES then
        Message("["..tostring(linec).."] "..line)
    else
        Message(line)
    end
    wait(1.5)
    linec = linec + 1
end
