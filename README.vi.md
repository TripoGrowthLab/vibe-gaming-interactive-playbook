# Vibe Gaming Interactive Playbook

[![Stars](https://img.shields.io/github/stars/TripoGrowthLab/vibe-gaming-interactive-playbook?style=flat-square&color=14c9e6)](https://github.com/TripoGrowthLab/vibe-gaming-interactive-playbook/stargazers) [![Prompt 1.1](https://img.shields.io/badge/Prompt-1.1-7c3aed?style=flat-square)](prompt/vibe-gaming.md) [![License: MIT](https://img.shields.io/badge/License-MIT-64748b?style=flat-square)](LICENSE) [![check](https://img.shields.io/github/actions/workflow/status/TripoGrowthLab/vibe-gaming-interactive-playbook/check.yml?branch=main&style=flat-square&label=examples%20build)](https://github.com/TripoGrowthLab/vibe-gaming-interactive-playbook/actions/workflows/check.yml)

<p>
  <a href="README.md"><img alt="English" src="https://img.shields.io/badge/English-64748b?style=flat-square"></a>
  <a href="README.zh-CN.md"><img alt="简体中文" src="https://img.shields.io/badge/%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87-64748b?style=flat-square"></a>
  <a href="README.ja.md"><img alt="日本語" src="https://img.shields.io/badge/%E6%97%A5%E6%9C%AC%E8%AA%9E-64748b?style=flat-square"></a>
  <a href="README.vi.md"><img alt="Tiếng Việt" src="https://img.shields.io/badge/Ti%E1%BA%BFng%20Vi%E1%BB%87t-✓-238636?style=flat-square"></a>
</p>

> Muốn tìm ý tưởng trước? Xem [Awesome 3D Prompts](https://github.com/TripoGrowthLab/awesome-3d-prompts) và [Awesome Opus 5.5 Prompts](https://github.com/TripoGrowthLab/awesome-opus-5-5-prompts).

<a href="https://studio.tripo3d.ai/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=vibe_gaming_interactive_handbook&amp;utm_content=readme_vi_hero"><img src="assets/hero.webp" width="100%" alt="Vibe Gaming Interactive Playbook: cùng một thế giới game ở bản greybox và bản đã có mô hình 3D hoàn chỉnh"></a>

**Một prompt. Một thư mục trống. Một game 3D để chia sẻ.**

Dán một prompt vào coding agent của bạn. Agent cùng bạn thiết kế một game nhỏ chạy trên trình duyệt, dựng bản greybox chơi được, liệt kê các mô hình 3D cần có, rồi thay vào những mô hình bạn tạo trong Tripo Studio. Bạn không cần viết code: chỉ chơi, góp ý và tạo mô hình.

**1 prompt · 6 giai đoạn · 3 game mẫu · 0 lần con người can thiệp trong cả ba game**

[Bắt đầu](#start-here) · [Prompt](#the-prompt) · [Game mẫu](#example-games) · [Lấy mô hình](#get-the-models) · [Thảo luận](https://github.com/TripoGrowthLab/vibe-gaming-interactive-playbook/discussions) · [Nhật ký thay đổi](prompt/CHANGELOG.md) · [Tripo Studio ↗](https://studio.tripo3d.ai/?utm_source=github&utm_medium=referral&utm_campaign=vibe_gaming_interactive_handbook&utm_content=readme_vi_nav)

<img src="assets/greybox-to-models.webp" width="100%" alt="Từng game mẫu chuyển từ greybox sang mô hình Tripo">

*Star repo này để dễ tìm lại. Muốn nhận tin khi có phiên bản prompt hay game mẫu mới, chọn **Watch → Custom → Releases**.*

<a id="start-here"></a>

## Bắt đầu

1. **Sao chép prompt.** Mở một thư mục trống trong coding agent (Claude Code, Codex, Cursor, …) và dán [prompt](#the-prompt).
2. **Trả lời, rồi chơi bản greybox.** Agent hỏi tối đa năm câu, viết một trang thiết kế và dựng game bằng các khối đơn giản. Chơi thử và nói chỗ nào chưa ổn; agent sẽ sửa và kiểm tra lại.
3. **Tạo mô hình, rồi thay vào.** Agent viết `assets.json` và một bảng liệt kê mọi mô hình, đánh dấu tối đa hai mô hình chính (hero) cần làm chi tiết cao. Tạo chúng theo [các bước trong Tripo Studio](prompt/tripo-studio-steps.md), xuất GLB, agent sẽ đưa vào game và so từng mô hình với bản greybox của nó.

Muốn xem kết quả trước khi bắt đầu? Clone repo này và chạy bất kỳ [game mẫu](#example-games) nào.

<a id="the-prompt"></a>

## Prompt

Phiên bản 1.1 · 2026-10-09 · khoảng 3.000 từ tiếng Anh. Sao chép khối bên dưới (nút sao chép ở góc trên bên phải), hoặc đọc trong [`prompt/vibe-gaming.md`](prompt/vibe-gaming.md). Prompt giữ nguyên tiếng Anh; nếu muốn agent trả lời bằng tiếng Việt, thêm một dòng "Trả lời tôi bằng tiếng Việt." ở cuối.

<details>
<summary><strong>Xem prompt</strong></summary>

<!-- prompt:start -->
```text
Help me make a small 3D browser game, step by step. I have never made a game before.

Before you write any code, ask me up to 5 short questions in one message: what the game is about, the one thing the player does, keyboard or phone or both, the art style, and anything I already have. Wait for my answers.

Once I have answered, start a git repository, save this whole prompt word for word to AGENTS.md, and add a CLAUDE.md that only says to read AGENTS.md. Keep a short PROGRESS.md: what is done, what we decided and what is next. Read both at the start of every stage, and commit at the end of every stage that works, so we can go back if a later change breaks something; each time, tell me the one command that takes us back to it.

Then work in stages. Stop at the end of every stage, tell me how to try it, and wait for my feedback:

1. Design — write GDD.md, one page: core loop, controls (keyboard and touch), win and lose, camera, and a table of every object on screen with an id, its size in metres and which way it faces. Keep it to one level and one core loop. Make up your own characters, names and level layout; do not copy any existing game, and do not make anything look like a well-known game character or item either. For every character that animates, list its states (for example idle, run, attack, hurt, knocked down) and when it switches between them, and say whether it is a person or another kind of body (an animal, a robot dog, a bug); only people get bones, so a body that is not a person is built from parts that move in code. If characters fight, write for each attack: which animation it uses, how much damage it does, and at what fraction of the animation the hit lands and ends. If a machine or object has parts that move, can be shot off or break apart, list its parts: what each part does, where it hinges, how much it can take, and what changes when it breaks. If parts can be swapped between machines or characters, give all of them the same set of slots, and for each slot write one attach point (where it sits, measured from the centre of the feet) and which way a part faces on that point.

2. Greybox — build it with Three.js and Vite, no game engine. Use only boxes, cylinders and capsules, sized from the table. Keep everything about how objects look in one place: a registry from id to a builder function, so a 3D model can replace any placeholder later without touching gameplay code. Build an object with parts as a group of named child placeholders, one per part, each turning around its own hinge, and let gameplay find parts by name. If parts can be swapped, hang each swappable part on a named attach point; swapping a part means hanging another part on that point and scaling it to fit the slot, and gameplay still finds parts by name. Every placeholder faces +Z. If the player jumps, make it feel good: a jump pressed just before landing still counts, a jump just after walking off a ledge still works, and holding the button jumps higher. If the player fights, make it feel good: a button pressed during an attack queues the next one, a hit freezes both fighters for a split second and pushes the target back, a character that was just hit cannot be hit again at once, and enemies take turns attacking instead of all at once. Show states on the placeholders (a colour or a lean) so I can see them. Put every number I might want to tune (speeds, sizes, camera, timings) in one config file, and add a hidden debug panel, opened with a key, with sliders for those numbers and readouts of FPS, draw calls, bounding boxes and each character's current state. Moving characters must look smooth on both 60 Hz and 120 Hz screens. Done when I can play a full round and restart, on desktop and on a phone. If a later change adds a new state, add it to GDD.md and tell me which animation it needs.

3. Asset list — write assets.json with one entry per id: its kind (prop, person or parts), size in metres (height for people, longest edge for everything else), a polygon budget in triangles (at least 500; at least 10000 for parts), and one English image prompt. Give every prompt the same art-style sentence, describe the shape and proportions it must have to fit its size, give visible details to the side the camera sees most (for a vehicle the player follows, its back) while still asking for one view of one object, and end it with "single isolated object, centered, on a plain white background". The ground, sky and edge of the level are part of the look too: say how each will be made (a Tripo entry or built in code), so none of them stays greybox. At most 8 entries; if several enemies share a shape, they share one entry, and one that differs only in colour gets a texture prompt on that entry instead of a new entry. A texture prompt repaints the whole model, so describe the whole object with every colour, not "the same but red"; a prop in one plain colour is tinted in code instead.

   - A person that animates must stand in a T-pose, facing the camera, with its head no more than a third of its height, arms long enough to reach mid-thigh, a body no wider than its shoulders, space between the arms, legs and body, and nothing loose that would flap or stick out (scarves, long hair, bandana tails, capes). Give it a list of animations taken only from these names in the Tripo library: idle, walk, run, jump, jump_down, fall, box_01, box_02, box_03, front_kick_01, slash, shoot, hit_to_body_01, hit_to_head, defeat_02, cheer. The name is only a label, so pick by what the motion is: jump has a long crouch before take-off, jump_down is a drop through the air, fall is tripping over onto the ground, defeat_02 is being knocked down, and the attacks are much slower than a game needs.

      If no name fits, write a one-line description of the motion instead, starting with its name and a colon (for example "dodge: a small character rolls forward and gets back up"); this works for people only, and it is reliable for motions on the ground; a motion in mid-air often comes out standing. Anything that only spins, bobs, squashes or flashes is animated in code, not in Tripo. A person who stays seated (a driver, a rider) keeps its legs and hips posed in code and uses animations for the upper body only; Text to Motion does not make good seated poses.

   - An object with parts (a machine, an animal or robot animal, anything that breaks apart) is one model that Tripo will split. List its parts in plain words (for example "left_cannon", "armour_plate", "front_left_leg"), at most 10, and if parts can be swapped, say which slot each part fits. Write the image prompt so that any central body is clearly its own piece, and every part in one main colour of its own, with a gap between parts. Parts that walk or swing are moved in code at their hinges, not rigged.

   - Mark at most two entries as hero: the player's character or vehicle and the main enemy, the ones the camera stays close to. A hero's image prompt keeps its name, colours and art-style sentence and adds what it is made of (painted metal, knitted wool, rubber), small details (rivets, stitching, buckles), decals or wear, and detail on the side the camera sees most, described as part of one front view of a single figure; never ask for a back view or several views. A hero gets 10000 triangles for a person and 15000–20000 for a model with parts; keep a hero's parts list to 6 or fewer, because Tripo merges neighbouring parts and cannot reduce small pieces much.

   - If I want more looks for the game (for example a skin switch, or an elite enemy), give the entry up to 4 styles, each one of classic, Wood (dark old wood), another style Tripo Studio lists under Create Your Own Texture Style, or "own image: [a close-up swatch of the material: colours and surface, no creature or object]" if I will make my own style picture and upload it; or "none". Pick only styles that suit the art style, and tell me what each will look like. Each style costs one more texture generation in Tripo.

   Add up the triangles and texture memory for the busiest moment on screen and say whether a phone can handle it. A Tripo model that is not a hero has colour textures only: one at the chosen resolution, or one per piece for a split model, smaller for small pieces. A hero has three 4K textures (colour, normal and metal-rough), shared by all its pieces. Count a split model that is not a hero at 1.5 times its budget, because filling its gaps adds triangles.

4. My turn — do not try to generate the models yourself. Give me one table with a row per entry: id, kind, hero or not, prompt, polygon budget, file name, animations or parts, and styles or texture prompt (or "none"). Then tell me to make them in Tripo Studio (https://studio.tripo3d.ai/workspace/generate?from=vgh-prompt-agent) by following these steps, which cover every kind of entry, heroes, styles, colour versions and export: https://github.com/TripoGrowthLab/vibe-gaming-interactive-playbook/blob/main/prompt/tripo-studio-steps.md . Wait until I say they are in.

5. Swap — load each GLB in place of its placeholder: scale it to the size in the list (people by height), sit it on the ground, and add an environment map so materials are not black. Keep every map a model comes with (colour, normal, metal-rough) and its metal and roughness values; only a model with a colour map alone gets roughness 1 and metalness 0. Render every model next to its placeholder and check it faces the same way; rotate it if it does not. Do this again whenever a model is replaced: a new version can face another way and has new UVs, so its style and colour files must be made again from it. First list what is really inside each file: animation names (Tripo often renames them: defeat_02 can come out as defeat_03, and a Text to Motion clip is named after the start of its description) and, for split models, every piece with its name, size and position. Match animations by the closest name. Match pieces by name first; a piece still called tripo_part_N belongs to a part only if its centre sits inside that part's placeholder, and to the body otherwise, so group them in code; print the pieces of each part and check them on a render before you move any hinge. The sizes stored in the file are not reliable, so recompute each bounding box before you measure anything. The order of meshes changes from file to file, so always match pieces by node name. Tell me what you matched and what is missing. Every piece keeps the whole model's origin: move each part's pivot to its hinge before you turn it, and since a few pieces may still have small holes, make sure nothing looks see-through when a part comes off (close it, show both sides, or put something dark behind it). Merge the pieces of each part into one mesh when they share one material (a hero with parts comes that way) or when draw calls hurt on a phone. If parts can be swapped between machines, line up where each part joins with its slot's attach point and scale it to fit the slot. When a swapped part has a different height, such as another machine's legs, seat everything above it on the new part's real height and hinges, not the old part's or the placeholder's, so nothing floats or sinks. If an entry has style versions, they have the same shape, but Tripo can change their UVs: compare each style's UVs with the default file's, and where they differ, use that style file's own mesh with its textures, cut into the same parts or bound to the same skeleton. List which maps each style file has; a style may come without a metal-rough map. Look at each version and tell me if one does not match its prompt, and add a button that switches skins, loading each style only the first time it is chosen. Never pair the shape data of one file with another file. Put a close-up of each model in the game next to how it looks in Tripo Studio; if colours look washed out or flat, fix the lighting (one main light that casts shadows, less flat ambient light, the right colour space), not the textures.

   Look at the frames of every animation before you use it: pick the part you need, find the moment a punch or kick really lands, and check arms and feet do not go through the body or clothes. Tripo animations are the same for every body shape, so on a character with a big head, a round belly or thick clothes the arms often sink into the hips or chest when they hang down and pass through the head when they go up. Measure this in code instead of judging it from small frames: in every frame of every animation, work out where the arm vertices really are and test whether they are inside the rest of the body (a winding-number test stays right on clothes and open meshes), using the T-pose as zero. Also look at close-ups from the front and from a 3/4 angle, including the armpits. If an arm goes in, fix it in code: after each animation frame, turn the upper arm outward at the shoulder just enough to clear the body (hips, belly, chest and head); ignore a few millimetres of sleeve resting on clothes, and never change a pose where the hands are meant to touch the body (pockets, hips). Tell me the worst depth for every animation before and after the fix.

   Play character animations by name with an AnimationMixer, blending between states, and keep the character in place so only gameplay code moves it: "stay in place" can still leave the body ahead of or behind its feet, so check the hips over the whole clip and centre them. Match walk and run playback speed to how fast the character really moves so the feet do not slide. If a character must do two things at once (run and shoot), play the legs from one animation and the upper body from another: the legs always face where it runs, the upper body twists toward the aim, and it backpedals when aiming behind. When one model is used by several characters at once, clone it with SkeletonUtils so each has its own skeleton. Check where characters stop and touch things using the models' real sizes, not the placeholders', colliding with simple shapes that follow each model's visible surface (a capsule for every character; for a rounded top, step it down and keep it inside the visible edge, so no one stands in the air) and never with a model's mesh itself; fit the shapes to the models, never stretch a model unevenly to fit an old shape, and measure every frame of a crash or knockdown so no character ends up inside what it hit. On a phone held upright, measure over a full round how much of the screen height the player takes up and how much of the screen is empty sky or background, and tell me the smallest and largest of each. Keep a button that switches between greybox and models. The colour tints and white hit flashes that showed states on the placeholders wash out painted models, so on models glow only the part that matters and brighten its own colours instead of adding white; then check that a landed hit is still easy to see and hear (a flash or sparks at the spot, a jolt of the part, a sound). Effects that shake a part must not move the point used for hit detection. Do not change gameplay code, not even to fix a bug; if timings, sizes or triggers need new numbers, tell me what and why, and wait for my yes. Tell me which files, animations or pieces did not load and why.

6. Publish — as a build step, shrink every GLB with glTF Transform (meshopt geometry, WebP textures no larger than they ever appear on screen) and load them with the matching decoders, leaving the files in public/assets as they are. Play a full round on the small files to check that every animation, piece and style still works. Compression changes a rigged model's bind matrices, so play every animation on both the small and the original files and compare how high the feet sit above the ground; anything measured from the bind pose (such as skeleton.pose()) should use the bones' own starting positions instead. Then tell me the total download size and how long the first screen takes to appear on a phone. Then help me put it on a free static host and give me the link. Ask me before you create any account, repository or public page.

Test your own work before you hand it to me: run the build, open the game, check the console for errors, and tell me exactly what you checked. If the game has fights or levels, write a small bot that plays a full round and report what it hit and whether it won, and a second one that plays badly (holds forward into walls and obstacles) to check nothing gets stuck. Wait for every test to finish before you reply; never start a test with & or in the background. Use only a browser that is already installed on this machine; never download one. If you cannot test something, tell me what to try myself. If something does not work, say so.
```
<!-- prompt:end -->

</details>

Agent làm việc qua sáu giai đoạn và dừng lại chờ bạn sau mỗi giai đoạn:

| Giai đoạn | Agent | Bạn |
| :--- | :--- | :--- |
| 1 Thiết kế | hỏi tối đa năm câu, viết `GDD.md` một trang | trả lời, duyệt |
| 2 Greybox | dựng game bằng hộp, trụ và viên nang, rồi tự kiểm tra bằng bot | chơi thử, nói chỗ nào chưa ổn |
| 3 Danh sách tài nguyên | viết `assets.json`: mọi mô hình, kích thước, ngân sách tam giác và prompt tạo | kiểm tra |
| 4 Đến lượt bạn | đưa bảng mô hình và chỉ bạn đến [các bước trong Tripo Studio](prompt/tripo-studio-steps.md) | tạo mô hình, xuất GLB |
| 5 Thay mô hình | nạp mô hình của bạn và so từng cái với bản greybox | chơi lại |
| 6 Phát hành | giúp bạn đưa game lên một hosting tĩnh miễn phí, hỏi trước khi tạo tài khoản hay trang công khai | nhận đường link |

Vì sao từng dòng trong prompt có mặt, và mỗi bản nháp đã thêm gì: [`prompt/CHANGELOG.md`](prompt/CHANGELOG.md).

<a id="example-games"></a>

## Game mẫu

Mỗi game được dựng từ một thư mục trống bằng một phiên bản của prompt này, do Claude Code với `claude-opus-5-5` thực hiện. Mã nguồn nằm trong [`examples/`](examples); mô hình Tripo không kèm theo, nên bản clone mới sẽ chạy ở chế độ greybox.

<table>
<tr>
<td width="33%" valign="top"><a href="https://handbook-snowdrift-dash.tripo.page/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=vibe_gaming_interactive_handbook&amp;utm_content=readme_vi_featured_ski"><img src="assets/games/ski.webp" width="280" alt="Snowdrift Dash"></a><br><strong><a href="#snowdrift-dash">Snowdrift Dash</a></strong><br><sub>Trượt tuyết đổ dốc vô tận · prompt v3.2</sub><br><a href="https://handbook-snowdrift-dash.tripo.page/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=vibe_gaming_interactive_handbook&amp;utm_content=readme_vi_featured_ski">Chơi ↗</a> · <a href="examples/ski">Mã nguồn</a></td>
<td width="33%" valign="top"><a href="https://handbook-lantern-alley.tripo.page/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=vibe_gaming_interactive_handbook&amp;utm_content=readme_vi_featured_lantern_alley"><img src="assets/games/lantern-alley.webp" width="280" alt="LANTERN ALLEY"></a><br><strong><a href="#lantern-alley">LANTERN ALLEY</a></strong><br><sub>Beat 'em up 3D kiểu arcade · prompt v2</sub><br><a href="https://handbook-lantern-alley.tripo.page/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=vibe_gaming_interactive_handbook&amp;utm_content=readme_vi_featured_lantern_alley">Chơi ↗</a> · <a href="examples/lantern-alley">Mã nguồn</a></td>
<td width="33%" valign="top"><a href="https://handbook-pit-nine.tripo.page/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=vibe_gaming_interactive_handbook&amp;utm_content=readme_vi_featured_pit_nine"><img src="assets/games/pit-nine.webp" width="280" alt="PIT NINE"></a><br><strong><a href="#pit-nine">PIT NINE</a></strong><br><sub>Bắn súng đấu trường góc nhìn từ trên · prompt v3</sub><br><a href="https://handbook-pit-nine.tripo.page/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=vibe_gaming_interactive_handbook&amp;utm_content=readme_vi_featured_pit_nine">Chơi ↗</a> · <a href="examples/pit-nine">Mã nguồn</a></td>
</tr>
</table>

**Con người can thiệp** nghĩa là gợi ý cách làm cho agent hoặc sửa giúp nó. Nói "tiếp đi", kể lại những gì bạn thấy khi chơi, hay chọn giữa các phương án agent đưa ra đều không tính.

<a id="snowdrift-dash"></a>

### Snowdrift Dash

Claude Code · `claude-opus-5-5` · prompt v3.2 · 8 mô hình · 0 lần con người can thiệp

| Greybox | Với mô hình Tripo |
| :---: | :---: |
| <img src="assets/games/ski-greybox.webp" width="400" alt="Snowdrift Dash ở bản greybox"> | <img src="assets/games/ski.webp" width="400" alt="Snowdrift Dash với mô hình Tripo"> |

Điều khiển người trượt tuyết xuống một con dốc vô tận; trụ càng lâu càng nhanh, va một lần là hết lượt. Người trượt tuyết có khung xương, dùng hai animation từ thư viện và một động tác lướt tạo bằng Text to Motion. [Chơi ↗](https://handbook-snowdrift-dash.tripo.page/?utm_source=github&utm_medium=referral&utm_campaign=vibe_gaming_interactive_handbook&utm_content=readme_vi_section_ski) · [Mã nguồn](examples/ski)

<a id="lantern-alley"></a>

### LANTERN ALLEY

Claude Code · `claude-opus-5-5` · prompt v2 · 10 mô hình, 6 nhân vật có khung xương · 0 lần con người can thiệp

| Greybox | Với mô hình Tripo |
| :---: | :---: |
| <img src="assets/games/lantern-alley-greybox.webp" width="400" alt="LANTERN ALLEY ở bản greybox"> | <img src="assets/games/lantern-alley.webp" width="400" alt="LANTERN ALLEY với mô hình Tripo"> |

Một anh hùng truyện tranh dọn sạch con hẻm qua bốn đợt côn đồ và tên trùm, với combo đấm, đá và đòn vừa chạy vừa đánh. Khi animation xuất ra bị đổi tên và chậm hơn nhịp của bản greybox vài lần, agent tự phát hiện, đo từng khung hình và đề xuất nhịp mới trước khi sửa bất cứ thứ gì. [Chơi ↗](https://handbook-lantern-alley.tripo.page/?utm_source=github&utm_medium=referral&utm_campaign=vibe_gaming_interactive_handbook&utm_content=readme_vi_section_lantern_alley) · [Mã nguồn](examples/lantern-alley)

<a id="pit-nine"></a>

### PIT NINE

Claude Code · `claude-opus-5-5` · prompt v3 · 8 mô hình, mỗi cái hai phong cách · 0 lần con người can thiệp

| Greybox | Với mô hình Tripo |
| :---: | :---: |
| <img src="assets/games/pit-nine-greybox.webp" width="400" alt="PIT NINE ở bản greybox"> | <img src="assets/games/pit-nine.webp" width="400" alt="PIT NINE với mô hình Tripo"> |

Chiến đấu với chó săn robot, rồi bắn tan một cỗ máy khổng lồ: mỗi bộ phận bị phá là nó mất một đòn tấn công. Chó săn và trùm được Tripo tách thành các bộ phận và chuyển động bằng code; một nút bấm đổi cả game sang phong cách texture thứ hai. [Chơi ↗](https://handbook-pit-nine.tripo.page/?utm_source=github&utm_medium=referral&utm_campaign=vibe_gaming_interactive_handbook&utm_content=readme_vi_section_pit_nine) · [Mã nguồn](examples/pit-nine)

Chạy một game mẫu:

```sh
git clone https://github.com/TripoGrowthLab/vibe-gaming-interactive-playbook.git
cd vibe-gaming-interactive-playbook/examples/ski
npm install && npm run dev
```

<a id="get-the-models"></a>

## Lấy mô hình

Mỗi game mẫu liệt kê mô hình của nó trong `assets.json`, kèm kích thước, ngân sách tam giác và đúng prompt đã dùng. [Tạo từng mô hình trong Tripo Studio](https://studio.tripo3d.ai/workspace/generate?utm_source=github&utm_medium=referral&utm_campaign=vibe_gaming_interactive_handbook&utm_content=readme_vi_models), xuất GLB, đặt tên file theo id và để vào `public/assets/` của game mẫu đó. Tải lại trang: mô hình nào bạn thêm sẽ thay bản greybox của nó, cái nào thiếu vẫn là greybox. README của từng game mẫu có hướng dẫn chi tiết.

Bản thân các mô hình Tripo không nằm trong repo này; mô hình bạn tạo sẽ hơi khác của chúng tôi, vì vậy ở giai đoạn 5 agent kiểm tra từng mô hình với bản greybox của nó.

<a id="show-your-game"></a>

## Khoe game của bạn

Đã làm được gì đó bằng prompt này? [Chia sẻ](https://github.com/TripoGrowthLab/vibe-gaming-interactive-playbook/issues/new?template=show-your-game.yml) kèm link và ảnh chụp màn hình. Gặp một bước mà agent hoặc Tripo Studio không làm đúng như prompt nói? [Báo lại](https://github.com/TripoGrowthLab/vibe-gaming-interactive-playbook/issues/new?template=prompt-feedback.yml); mỗi dòng trong prompt đều đến từ một báo cáo như vậy. Xem [hướng dẫn đóng góp](CONTRIBUTING.md).

<a id="built-with"></a>

## Công cụ sử dụng

- [Tripo Studio](https://studio.tripo3d.ai/?utm_source=github&utm_medium=referral&utm_campaign=vibe_gaming_interactive_handbook&utm_content=readme_vi_built_with): mọi mô hình 3D trong các game mẫu
- [Claude Code](https://github.com/anthropics/claude-code) với `claude-opus-5-5`: coding agent đã dựng cả ba game từ prompt
- [three.js](https://threejs.org): dựng hình, animation và nạp mô hình
- [Vite](https://vite.dev): dev server và build
- [Playwright](https://playwright.dev): các bài chơi thử và ảnh chụp do agent tự làm, trong `tools/` của từng game mẫu
- [glTF Transform](https://gltf-transform.dev): kiểm tra mô hình trong LANTERN ALLEY

---

Do [TripoGrowthLab](https://github.com/TripoGrowthLab) tuyển chọn. Ảnh bìa là ảnh minh hoạ ý tưởng do AI tạo; ảnh chụp game là ảnh thật từ các game mẫu. [Giấy phép MIT](LICENSE) áp dụng cho prompt, mã nguồn mẫu và tài liệu của chúng tôi; không áp dụng cho thương hiệu Tripo hay mô hình bạn tạo ra. Xem [quyền sử dụng](RIGHTS.md).
