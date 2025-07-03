# bouncingburger_jimenezkennethlorenzo
import tkinter as tk

root = tk.Tk()
root.title("Tower Burger - Kenzo Jimenez")
canvas = tk.Canvas(root, width=600, height=500, bg="#f5f5dc")
canvas.pack()

# Starting position
x0, y0 = 240, 0
dx = 20
dy = 10
direction = 1  # 1 for right, -1 for left

# Draw tower burger layers
def draw_tower_burger(x, y):
    parts = []

    # Top bun with sesame seeds
    top_bun = canvas.create_oval(x, y, x+120, y+30, fill="#D2691E", outline="#8B4513", width=2)
    for i in range(5):
        parts.append(canvas.create_oval(x+15+i*20, y+10, x+20+i*20, y+15, fill="white", outline=""))

    # Add each layer down the stack
    y += 30
    bacon = canvas.create_rectangle(x+10, y, x+110, y+10, fill="#a52a2a", outline="#7b1b1b")
    y += 10
    egg = canvas.create_oval(x+20, y, x+100, y+20, fill="#fffacd", outline="#e6d000")
    y += 20
    patty1 = canvas.create_rectangle(x+15, y, x+105, y+15, fill="#5c4033", outline="#3e2723")
    y += 15
    cheese = canvas.create_polygon(x+20, y, x+100, y, x+90, y+15, x+30, y+15, fill="#ffcc00", outline="#d4af37")
    y += 15
    tomato = canvas.create_rectangle(x+20, y, x+100, y+10, fill="#ff6347", outline="#cc4125")
    y += 10
    lettuce = canvas.create_rectangle(x+10, y, x+110, y+10, fill="#7CFC00", outline="#5cbf00")
    y += 10
    patty2 = canvas.create_rectangle(x+15, y, x+105, y+15, fill="#4b2e2e", outline="#2d1a1a")
    y += 15
    bottom_bun = canvas.create_oval(x, y, x+120, y+20, fill="#D2691E", outline="#8B4513", width=2)

    # Name label
    name = canvas.create_text(x+60, y-40, text="Kenzo Jimenez", font=("Arial", 12, "bold"), fill="black")

    parts.extend([top_bun, bacon, egg, patty1, cheese, tomato, lettuce, patty2, bottom_bun, name])
    return parts

# Draw once at initial position
burger_parts = draw_tower_burger(x0, y0)

def zigzag_move():
    global x0, y0, dx, dy, direction, burger_parts

    # Move all parts
    for part in burger_parts:
        canvas.move(part, dx * direction, dy)

    x0 += dx * direction
    y0 += dy

    # Reverse direction when reaching sides
    if x0 <= 50 or x0 >= 430:
        direction *= -1

    # Reset to top when reaching bottom
    if y0 > 500:
        for part in burger_parts:
            canvas.delete(part)
        x0, y0 = 240, 0
        burger_parts[:] = draw_tower_burger(x0, y0)

    canvas.after(50, zigzag_move)

# Start animation
zigzag_move()
root.mainloop()![kenlooo](https://github.com/user-attachments/assets/9afcdb2d-98a6-4d6c-86cd-23e333145ff1)


https://github.com/user-attachments/assets/dba3c710-4a3f-4b6d-b0a1-e4f0140d10f0

