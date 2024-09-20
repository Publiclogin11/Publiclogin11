import pygame
import random
import time

# Initialize Pygame
pygame.init()

# Screen dimensions
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Proposal Animation")

# Colors
WHITE = (255, 255, 255)
RED = (255, 0, 0)

# Font
font = pygame.font.Font(None, 48)

def draw_heart(x, y):
    pygame.draw.circle(screen, RED, (x, y), 30)
    pygame.draw.circle(screen, RED, (x + 30, y), 30)
    pygame.draw.polygon(screen, RED, [(x, y), (x + 15, y + 50), (x + 30, y)])

def display_text(text, x, y):
    text_surface = font.render(text, True, WHITE)
    screen.blit(text_surface, (x, y))

def main():
    clock = pygame.time.Clock()
    running = True
    proposal_text = "Hey [Her Name], will you be my girlfriend?"
    
    while running:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False

        screen.fill((0, 0, 0))

        # Display text with typing effect
        for i in range(len(proposal_text) + 1):
            screen.fill((0, 0, 0))
            display_text(proposal_text[:i], 100, HEIGHT // 2)
            draw_heart(100, HEIGHT // 2 + 50)
            pygame.display.flip()
            time.sleep(0.1)

        # Show final heart animation
        for i in range(10):
            screen.fill((0, 0, 0))
            draw_heart(100, HEIGHT // 2 + 50)
            pygame.display.flip()
            time.sleep(0.3)

        time.sleep(2)  # Pause before closing
        running = False

    pygame.quit()

# Run the main function
if __name__ == "__main__":
    main()
