local PERCENT_TO_BUY_ARMOR   = 30         --\\ percent of armor left that u want to buy
local COMMAND_TO_STOP_BUYING = ('/e stop') --\\ message to stop buying

------------------------
------------------------

function announce(title,text,time)
    game.StarterGui:SetCore("SendNotification", {
        Title = title;
        Text = text;
        Duration = time;
    })
end
announce('Autobuying armor at %' .. tostring(PERCENT_TO_BUY_ARMOR), 'chat ' .. COMMAND_TO_STOP_BUYING .. ' to stop', 8)

local Stopped = false
local Player = game.Players.LocalPlayer
function Main1()
    while wait() do
        local function AutoArmor()
            local Origin = Player.Character.HumanoidRootPart.CFrame
            local Armor = Player.Character.BodyEffects.Armor
            if Armor.Value <= PERCENT_TO_BUY_ARMOR and Stopped == false then
                repeat
                    wait()    
                    Player.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Ignored.Shop["[Medium Armor] - $1000"].Head.CFrame
                    fireclickdetector(game:GetService("Workspace").Ignored.Shop["[Medium Armor] - $1000"].ClickDetector)
                until Armor.Value == 100 or Player.DataFolder.Currency.Value < 1000
                Player.Character.HumanoidRootPart.CFrame = Origin
            end
        end
        local s,e = pcall(AutoArmor)
    end
end
function Main2()
    Player.Chatted:Connect(function(msg)
        if msg == COMMAND_TO_STOP_BUYING and Stopped == false then
            Stopped = true
            announce('stopped buying', '',5)
        end
    end)
end
coroutine.resume(coroutine.create(Main1))
coroutine.resume(coroutine.create(Main2))
