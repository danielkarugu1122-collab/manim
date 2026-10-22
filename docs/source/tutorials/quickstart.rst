from manim import *

class KCSEMathVisualizer(Scene):
    def construct(self):
        # 1. Title
        title = Text("Graph Transformation: Parabolas", font_size=32)
        title.to_edge(UP)
        self.play(Write(title))

        # 2. Setup Axes
        axes = Axes(
            x_range=[-3, 3, 1],
            y_range=[-1, 9, 1],
            x_length=6,
            y_length=5,
            axis_config={"color": BLUE},
        )
        axes_labels = axes.get_axis_labels(x_label="x", y_label="y")

        self.play(Create(axes), Write(axes_labels))

        # 3. Plot initial graph: y = x^2
        parabola = axes.plot(lambda x: x**2, color=YELLOW)
        parabola_label = axes.get_graph_label(parabola, label="y = x^2", x_val=2)

        self.play(Create(parabola), Write(parabola_label))
        self.wait(1)

        # 4. Transform to a shifted graph: y = (x-1)^2 + 2
        shifted_parabola = axes.plot(lambda x: (x-1)**2 + 2, color=GREEN)
        shifted_label = axes.get_graph_label(shifted_parabola, label="y = (x-1)^2 + 2", x_val=2, direction=UP)

        self.play(
            Transform(parabola, shifted_parabola),
            Transform(parabola_label, shifted_label),
            run_time=2
        )
        self.wait(2)
