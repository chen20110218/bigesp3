-- 第一部分：全屏卡密验证UI
local CoreGui = game:GetService("CoreGui")
local UserInputService = game:GetService("UserInputService")

-- 创建主UI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "FullScreenKeyAuth"
ScreenGui.Parent = CoreGui
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
ScreenGui.DisplayOrder = 999
ScreenGui.IgnoreGuiInset = true  -- 真正全屏覆盖

-- 全屏背景框架
local MainFrame = Instance.new("Frame")
MainFrame.Name = "FullScreenFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)  -- 纯白背景
MainFrame.BorderSizePixel = 0
MainFrame.Size = UDim2.new(1, 0, 1, 0)
MainFrame.Position = UDim2.new(0, 0, 0, 0)

-- 内容容器（居中）
local ContentFrame = Instance.new("Frame")
ContentFrame.Name = "Content"
ContentFrame.Parent = MainFrame
ContentFrame.AnchorPoint = Vector2.new(0.5, 0.5)
ContentFrame.Position = UDim2.new(0.5, 0, 0.5, 0)
ContentFrame.Size = UDim2.new(0.85, 0, 0.35, 0)
ContentFrame.BackgroundTransparency = 1

-- 标题文本
local TitleLabel = Instance.new("TextLabel")
TitleLabel.Name = "Title"
TitleLabel.Parent = ContentFrame
TitleLabel.Size = UDim2.new(1, 0, 0.3, 0)
TitleLabel.Position = UDim2.new(0, 0, 0, 0)
TitleLabel.BackgroundTransparency = 1
TitleLabel.Text = "安全验证系统"
TitleLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
TitleLabel.TextScaled = true
TitleLabel.Font = Enum.Font.SourceSansBold

-- 提示文本
local PromptLabel = Instance.new("TextLabel")
PromptLabel.Name = "Prompt"
PromptLabel.Parent = ContentFrame
PromptLabel.Size = UDim2.new(1, 0, 0.2, 0)
PromptLabel.Position = UDim2.new(0, 0, 0.3, 0)
PromptLabel.BackgroundTransparency = 1
PromptLabel.Text = "请输入您的卡密"
PromptLabel.TextColor3 = Color3.fromRGB(50, 50, 50)
PromptLabel.TextScaled = true
PromptLabel.Font = Enum.Font.SourceSans

-- 输入框
local InputBox = Instance.new("TextBox")
InputBox.Name = "KeyInput"
InputBox.Parent = ContentFrame
InputBox.Size = UDim2.new(1, 0, 0.2, 0)
InputBox.Position = UDim2.new(0, 0, 0.5, 0)
InputBox.BackgroundColor3 = Color3.fromRGB(245, 245, 245)
InputBox.Text = ""
InputBox.PlaceholderText = "在此输入卡密..."
InputBox.TextColor3 = Color3.fromRGB(0, 0, 0)
InputBox.TextScaled = true
InputBox.ClearTextOnFocus = false
InputBox.Font = Enum.Font.SourceSans

-- 输入框圆角
local InputCorner = Instance.new("UICorner")
InputCorner.CornerRadius = UDim.new(0.1, 0)
InputCorner.Parent = InputBox

-- 输入框边框
local InputStroke = Instance.new("UIStroke")
InputStroke.Parent = InputBox
InputStroke.Color = Color3.fromRGB(200, 200, 200)
InputStroke.Thickness = 2

-- 验证函数
local function validateKey(input)
    local correctKey = "鸟帝天下第一"
    return input == correctKey
end

-- 全局标志，指示验证是否通过
_G.KeyAuthPassed = false

-- 处理验证逻辑
local function handleValidation()
    if validateKey(InputBox.Text) then
        PromptLabel.Text = "验证成功！正在加载..."
        PromptLabel.TextColor3 = Color3.fromRGB(0, 180, 0)
        
        -- 更新输入框状态
        InputBox.Text = "✓ 验证通过"
        InputBox.TextColor3 = Color3.fromRGB(0, 180, 0)
        InputBox.BackgroundColor3 = Color3.fromRGB(230, 255, 230)
        InputBox.TextEditable = false
        
        -- 设置全局验证通过标志
        _G.KeyAuthPassed = true
        
        -- 1秒后淡出UI
        wait(1)
        
        -- 淡出动画
        for i = 1, 10 do
            MainFrame.BackgroundTransparency = i/10
            wait(0.05)
        end
        
        -- 移除UI
        ScreenGui:Destroy()
        
        return true
    else
        PromptLabel.Text = "卡密错误，请重试"
        PromptLabel.TextColor3 = Color3.fromRGB(180, 0, 0)
        
        -- 抖动动画效果
        local originalPos = ContentFrame.Position
        for i = 1, 3 do
            ContentFrame.Position = originalPos + UDim2.new(0, 5, 0, 0)
            wait(0.05)
            ContentFrame.Position = originalPos + UDim2.new(0, -5, 0, 0)
            wait(0.05)
        end
        ContentFrame.Position = originalPos
        
        InputBox.Text = ""
        return false
    end
end

-- 绑定回车键验证
InputBox.FocusLost:Connect(function(enterPressed)
    if enterPressed then
        handleValidation()
    end
end)

-- 手机端适配：添加虚拟键盘完成按钮
if UserInputService.TouchEnabled then
    InputBox.TextInputType = Enum.TextInputType.Default
end

-- 防止玩家关闭GUI
ScreenGui.ResetOnSpawn = false

-- 等待验证通过
while not _G.KeyAuthPassed do
    wait(0.1)
end

-- 当验证通过后，脚本会继续执行下面的第二部分脚本
--------------------------------------------------
-- 第二部分脚本可以直接放在这里 --
--------------------------------------------------
print("✅ 等待结束，开始执行主脚本...")

-- 在这里拼接你的主脚本
-- 你的主脚本内容从这里开始...
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local GuiService = game:GetService("GuiService")

-- 创建ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "ColorChangingText"
screenGui.ResetOnSpawn = false
screenGui.DisplayOrder = 999  -- 确保在最前面显示
screenGui.Parent = LocalPlayer:WaitForChild("PlayerGui")

-- 创建文本标签
local textLabel = Instance.new("TextLabel")
textLabel.Size = UDim2.new(1, 0, 1, 0)
textLabel.Position = UDim2.new(0, 0, 0, 0)
textLabel.BackgroundTransparency = 1
textLabel.Text = "🐦欢迎使用ESP，正在为您扫描全图🐦"
textLabel.Font = Enum.Font.SourceSansBold
textLabel.TextSize = 36
textLabel.TextColor3 = Color3.new(1, 1, 1)
textLabel.TextStrokeTransparency = 0.5
textLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
textLabel.ZIndex = 10
textLabel.Parent = screenGui

-- 调整文本位置使其居中
textLabel.AnchorPoint = Vector2.new(0.5, 0.5)
textLabel.Position = UDim2.new(0.5, 0, 0.5, 0)

-- 颜色变化函数
local function changeColor()
    local time = 0
    local duration = 5 -- 5秒
    
    while time < duration do
        local hue = (tick() * 24) % 360
        textLabel.TextColor3 = Color3.fromHSV(hue/360, 1, 1)
        wait(0.05)
        time = time + 0.05
    end
    
    -- 5秒后移除
    screenGui:Destroy()
end

-- 启动颜色变化
coroutine.wrap(changeColor)()

-- ▼▼▼ 以下是第二个ESP脚本 ▼▼▼
-- 等待5秒脚本（适用于Delta注入器）
local waitTime = 5 -- 等待时间（秒）
local startTime = tick()

print("⏳ 脚本将在 "..waitTime.." 秒后开始执行...")

while tick() - startTime < waitTime do
    -- 每隔1秒打印一次剩余时间
    local remaining = math.floor(waitTime - (tick() - startTime))
    if remaining ~= lastRemaining then
        print("🕒 剩余时间: "..remaining.."秒")
        lastRemaining = remaining
    end
    wait(0.1)
end

print("✅ 等待结束，开始执行主脚本...")

-- 在这里拼接你的主脚本
-- 你的主脚本内容从这里开始...
-- ===== 原始ESP脚本保持不变 =====
-- 高级ESP脚本 v2.4 - 优化版（距离7米内关闭高亮）
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local LocalPlayer = Players.LocalPlayer

-- ===== 配置区域 =====
local SETTINGS = {
    -- 敌人设置
    ENEMY_TAGS = {"Rake", "Monster", "Enemy"},
    ENEMY_COLOR = Color3.fromRGB(255, 50, 50),
    
    -- 玩家设置
    PLAYER_COLOR = Color3.fromRGB(50, 150, 255),
    TEAM_COLOR = Color3.fromRGB(50, 255, 100),
    
    -- 显示设置
    SHOW_HEALTH = true,
    SHOW_DISTANCE = true,
    SHOW_TRACER = true,
    TRACER_COLOR = Color3.fromRGB(0, 150, 255),
    ENEMY_TRACER_COLOR = Color3.fromRGB(255, 50, 50),
    TRACER_THICKNESS = 0.1,
    
    -- 高级设置
    MAX_DISTANCE = 1000,  -- 已修改为1000单位
    HEALTH_TEXT_SIZE = 16,
    DISTANCE_TEXT_SIZE = 14,
    NAME_TEXT_SIZE = 18,
    UPDATE_RATE = 0.005,
    
    -- 新增设置
    SCAN_INTERVAL = 5,
    TRACER_FOR_ENEMIES = true,
    
    -- 新增：高亮关闭距离 (改为7米)
    HIGHLIGHT_DISABLE_DISTANCE = 7  -- 距离小于7米时关闭高亮
}

-- ===== 核心功能 =====
local espCache = {}
local lastScanTime = 0

local function createESP(target)
    if not target or not target:FindFirstChild("HumanoidRootPart") then return end
    
    if espCache[target] then return end
    
    local isEnemy = false
    local isTeammate = false
    local espColor = SETTINGS.PLAYER_COLOR
    
    for _, tag in ipairs(SETTINGS.ENEMY_TAGS) do
        if target.Name:find(tag) or target:FindFirstChild(tag) then
            isEnemy = true
            espColor = SETTINGS.ENEMY_COLOR
            break
        end
    end
    
    if not isEnemy and target:FindFirstChild("Team") then
        if LocalPlayer.Team and target.Team == LocalPlayer.Team then
            isTeammate = true
            espColor = SETTINGS.TEAM_COLOR
        end
    end
    
    local highlight = Instance.new("Highlight")
    highlight.Name = "AdvancedESP_Highlight"
    highlight.FillColor = espColor
    highlight.OutlineColor = Color3.fromRGB(255, 255, 255)
    highlight.FillTransparency = 0.3
    highlight.OutlineTransparency = 0
    highlight.Parent = target
    
    local billboard = Instance.new("BillboardGui")
    billboard.Name = "AdvancedESP_Billboard"
    billboard.Adornee = target.HumanoidRootPart
    billboard.Size = UDim2.new(0, 150, 0, 60)
    billboard.StudsOffset = Vector3.new(0, 3.5, 0)
    billboard.AlwaysOnTop = true
    billboard.Parent = target
    
    local distanceText = Instance.new("TextLabel")
    distanceText.Name = "ESP_Distance"
    distanceText.Size = UDim2.new(1, 0, 0.3, 0)
    distanceText.Position = UDim2.new(0, 0, 0, 0)
    distanceText.BackgroundTransparency = 1
    distanceText.TextColor3 = Color3.fromRGB(200, 200, 255)
    distanceText.TextStrokeTransparency = 0.5
    distanceText.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
    distanceText.TextSize = SETTINGS.DISTANCE_TEXT_SIZE
    distanceText.Font = Enum.Font.SourceSansBold
    distanceText.TextXAlignment = Enum.TextXAlignment.Center
    distanceText.Parent = billboard
    
    local healthText = Instance.new("TextLabel")
    healthText.Name = "ESP_Health"
    healthText.Size = UDim2.new(1, 0, 0.4, 0)
    healthText.Position = UDim2.new(0, 0, 0.3, 0)
    healthText.BackgroundTransparency = 1
    healthText.TextColor3 = Color3.fromRGB(255, 255, 255)
    healthText.TextStrokeTransparency = 0.5
    healthText.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
    healthText.TextSize = SETTINGS.HEALTH_TEXT_SIZE
    healthText.Font = Enum.Font.SourceSansBold
    healthText.TextXAlignment = Enum.TextXAlignment.Center
    healthText.Parent = billboard
    
    local nameText = Instance.new("TextLabel")
    nameText.Name = "ESP_Name"
    nameText.Size = UDim2.new(1, 0, 0.3, 0)
    nameText.Position = UDim2.new(0, 0, 0.7, 0)
    nameText.BackgroundTransparency = 1
    nameText.TextColor3 = espColor
    nameText.TextStrokeTransparency = 0.5
    nameText.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
    nameText.TextSize = SETTINGS.NAME_TEXT_SIZE
    nameText.Font = Enum.Font.SourceSansBold
    nameText.TextXAlignment = Enum.TextXAlignment.Center
    nameText.Parent = billboard
    
    local tracer
    if SETTINGS.SHOW_TRACER and (not isEnemy or SETTINGS.TRACER_FOR_ENEMIES) then
        local startAttachment = Instance.new("Attachment")
        startAttachment.Name = "TracerStart"
        startAttachment.Parent = workspace.CurrentCamera
        
        local endAttachment = Instance.new("Attachment")
        endAttachment.Name = "TracerEnd"
        endAttachment.Parent = target.HumanoidRootPart
        
        tracer = Instance.new("Beam")
        tracer.Name = "ESP_Tracer"
        tracer.Attachment0 = startAttachment
        tracer.Attachment1 = endAttachment
        tracer.Color = ColorSequence.new(isEnemy and SETTINGS.ENEMY_TRACER_COLOR or SETTINGS.TRACER_COLOR)
        tracer.Width0 = SETTINGS.TRACER_THICKNESS
        tracer.Width1 = SETTINGS.TRACER_THICKNESS * 0.8
        tracer.LightEmission = 0.8
        tracer.Transparency = NumberSequence.new(0.5)
        tracer.FaceCamera = true
        tracer.Parent = target.HumanoidRootPart
    end
    
    espCache[target] = {
        highlight = highlight,
        billboard = billboard,
        tracer = tracer,
        humanoid = target:FindFirstChildOfClass("Humanoid"),
        rootPart = target.HumanoidRootPart,
        startAttachment = tracer and tracer.Attachment0,
        endAttachment = tracer and tracer.Attachment1,
        isEnemy = isEnemy
    }
end

local function fullScan()
    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= LocalPlayer and player.Character then
            createESP(player.Character)
        end
    end
    
    for _, descendant in ipairs(workspace:GetDescendants()) do
        if descendant:IsA("Model") and descendant:FindFirstChild("HumanoidRootPart") then
            for _, tag in ipairs(SETTINGS.ENEMY_TAGS) do
                if descendant.Name:find(tag) or descendant:FindFirstChild(tag) then
                    createESP(descendant)
                    break
                end
            end
        end
    end
end

-- ===== 更新循环 =====
local lastUpdate = 0
local espEnabled = true  -- 新增：ESP开关状态变量

RunService.Heartbeat:Connect(function(deltaTime)
    lastUpdate = lastUpdate + deltaTime
    lastScanTime = lastScanTime + deltaTime
    
    -- 如果ESP被禁用，直接跳过所有更新
    if not espEnabled then return end
    
    if lastScanTime >= SETTINGS.SCAN_INTERVAL then
        lastScanTime = 0
        fullScan()
    end
    
    if lastUpdate < SETTINGS.UPDATE_RATE then return end
    lastUpdate = 0
    
    if not LocalPlayer.Character or not LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then return end
    local localRoot = LocalPlayer.Character.HumanoidRootPart
    
    for target, data in pairs(espCache) do
        if not target.Parent then
            if data.highlight then data.highlight:Destroy() end
            if data.billboard then data.billboard:Destroy() end
            if data.tracer then data.tracer:Destroy() end
            espCache[target] = nil
        else
            local distance = (data.rootPart.Position - localRoot.Position).Magnitude
            local distanceInMeters = distance / 3.571  -- 转换为米
            local shouldShow = distance <= SETTINGS.MAX_DISTANCE
            
            -- 显示/隐藏Billboard和Tracer
            data.billboard.Enabled = shouldShow
            if data.tracer then
                data.tracer.Enabled = shouldShow
                if data.startAttachment then
                    data.startAttachment.WorldPosition = localRoot.Position - Vector3.new(0, 1.5, 0)
                end
            end
            
            -- ===== 优化：距离小于7米时关闭高亮 =====
            if shouldShow then
                -- 当距离小于配置值时关闭高亮
                if distanceInMeters < SETTINGS.HIGHLIGHT_DISABLE_DISTANCE then
                    data.highlight.Enabled = false
                else
                    data.highlight.Enabled = true
                end
            else
                data.highlight.Enabled = false
            end
            
            -- 更新文本信息
            if shouldShow then
                if SETTINGS.SHOW_DISTANCE then
                    data.billboard.ESP_Distance.Text = string.format("%.1fm", distanceInMeters)
                else
                    data.billboard.ESP_Distance.Text = ""
                end
                
                if SETTINGS.SHOW_HEALTH and data.humanoid then
                    data.billboard.ESP_Health.Text = string.format("HP: %d/%d", 
                        math.floor(data.humanoid.Health), 
                        math.floor(data.humanoid.MaxHealth))
                else
                    data.billboard.ESP_Health.Text = ""
                end
                
                data.billboard.ESP_Name.Text = target.Name
            end
        end
    end
end)

-- ===== 初始化和事件监听 =====
fullScan()

Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        if espEnabled then  -- 新增：仅在ESP启用时创建
            createESP(character)
        end
    end)
end)

workspace.DescendantAdded:Connect(function(descendant)
    if descendant:IsA("Model") and descendant:FindFirstChild("HumanoidRootPart") then
        for _, tag in ipairs(SETTINGS.ENEMY_TAGS) do
            if descendant.Name:find(tag) or descendant:FindFirstChild(tag) then
                if espEnabled then  -- 新增：仅在ESP启用时创建
                    createESP(descendant)
                end
                break
            end
        end
    end
end)

LocalPlayer.CharacterRemoving:Connect(function()
    for _, data in pairs(espCache) do
        if data.highlight then data.highlight:Destroy() end
        if data.billboard then data.billboard:Destroy() end
        if data.tracer then data.tracer:Destroy() end
    end
    espCache = {}
end)

-- ===== 新增：ESP开关GUI =====
local function createToggleGUI()
    -- 创建主GUI容器
    local screenGui = Instance.new("ScreenGui")
    screenGui.Name = "ESPToggleGUI"
    screenGui.ResetOnSpawn = false
  screenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
    
    -- 主框架
    local mainFrame = Instance.new("Frame")
    mainFrame.Name = "MainFrame"
    mainFrame.Size = UDim2.new(0, 100, 0, 40)
    mainFrame.Position = UDim2.new(1, -110, 0, 20)  -- 右上角位置
    mainFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 30)
    mainFrame.BackgroundTransparency = 0.3
    mainFrame.BorderSizePixel = 0
    mainFrame.Parent = screenGui
    
    -- 圆角效果
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0.2, 0)
    corner.Parent = mainFrame
    
    -- 开关按钮
    local toggleButton = Instance.new("TextButton")
    toggleButton.Name = "ToggleButton"
    toggleButton.Size = UDim2.new(0.9, 0, 0.7, 0)
    toggleButton.Position = UDim2.new(0.05, 0, 0.15, 0)
    toggleButton.BackgroundColor3 = espEnabled and Color3.fromRGB(50, 200, 80) or Color3.fromRGB(200, 50, 50)
    toggleButton.Text = espEnabled and "ESP开启中" or "ESP关闭中"
    toggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    toggleButton.TextSize = 16
    toggleButton.Font = Enum.Font.SourceSansBold
    toggleButton.AutoButtonColor = true
    toggleButton.Parent = mainFrame
    
    -- 按钮圆角
    local buttonCorner = Instance.new("UICorner")
    buttonCorner.CornerRadius = UDim.new(0.15, 0)
    buttonCorner.Parent = toggleButton
    
    -- 开关功能实现
    toggleButton.MouseButton1Click:Connect(function()
        espEnabled = not espEnabled
        
        -- 更新按钮状态
        toggleButton.BackgroundColor3 = espEnabled and Color3.fromRGB(50, 200, 80) or Color3.fromRGB(200, 50, 50)
        toggleButton.Text = espEnabled and "ESP开启中" or "ESP关闭中"
        
        if not espEnabled then
            -- 禁用ESP时清除所有当前ESP元素
            for _, data in pairs(espCache) do
                if data.highlight then data.highlight:Destroy() end
                if data.billboard then data.billboard:Destroy() end
                if data.tracer then data.tracer:Destroy() end
            end
            espCache = {}
        else
            -- 重新启用时执行全扫描
            fullScan()
        end
    end)
    
    -- 可拖动功能
    local dragging
    local dragInput
    local dragStart
    local startPos
    
    local function update(input)
        local delta = input.Position - dragStart
        mainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
    
    mainFrame.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            dragging = true
            dragStart = input.Position
            startPos = mainFrame.Position
            
            input.Changed:Connect(function()
                if input.UserInputState == Enum.UserInputState.End then
                    dragging = false
                end
            end)
        end
    end)
    
    mainFrame.InputChanged:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseMovement then
            dragInput = input
        end
    end)
    
    game:GetService("UserInputService").InputChanged:Connect(function(input)
        if input == dragInput and dragging then
            update(input)
        end
    end)
    
    return screenGui
end

-- 创建开关GUI
createToggleGUI()
