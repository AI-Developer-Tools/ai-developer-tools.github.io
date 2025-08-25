---
title: "CMU 17-316/616: AI Tools for Software Development"
hide:
  - navigation
---

<img src="assets/images/logos/logo316.png" width="80%" alt="TODO">

# 17-316/616: AI Tools for Software Development

Students will learn how to use AI-based developer tools across the software development lifecycle, for example in coding, code reviewing, project management, automated testing, and security. The course will require significant software development practice, both with and without AI tools. Students will use their experiences to analyze the impact of AI tools on software productivity across individuals, teams, and organizations.

## This Week

<div id="this-week">

{%- set this_week = extra.this_week -%}

<div class="card">
    <div class="header">
        Class & Readings
    </div>
    <div class="content">
        {% if this_week.lectures %}
            {% for lecture in this_week.lectures %}
                <div class="lecture-name">
                    {{ lecture.name }}
                </div>
                <div class="lecture-date">
                    <span class="material-symbols-outlined">calendar_month</span>
                    {{ lecture.date }}
                </div>

                {% if lecture.link != "" %}
                <a class="label label-gold" href="{{lecture.link}}" target="_blank">
                    <span class="material-symbols-outlined">slideshow</span>
                    Slides
                </a>
                {% endif %}

                {% if lecture.reading %}
                    <a class="label label-blue" href="{{lecture.reading.link}}" target="_blank">
                        <span class="material-symbols-outlined">link</span>
                        {{lecture.reading.name}}
                    </a>
                    {% if lecture.reading.name2 %}
                        {% if lecture.reading.name2 != "" %}
                            <a class="label label-blue" href="{{lecture.reading.link2}}" target="_blank">
                            <span class="material-symbols-outlined">link</span>
                                {{lecture.reading.name2}}
                            </a>
                        {% endif %}
                    {% endif %}
                {% endif %}
                {% if not loop.last %}
                <hr/>
                {% endif %}
            {% endfor %}
        {% else %}
            None!
        {% endif %}
    </div>

</div>

<div class="card">
    <div class="header">
        Office Hours
    </div>
    <div class="content">
        <p>Andrew Begel's Office Hours are in TCS 441. Austin Henley's Office Hours will be in TCS 445. See <a href="#class-calendar">class calendar</a> below for the times!</p>
    </div>

</div>

<div class="card">
    <div class="header">
        Current Assignment
    </div>
    <div class="content">
        {% if this_week.last_homework %}
            <div class="homework-name">
                {{ this_week.last_homework.name }}
            </div>

            {% if this_week.last_homework.deadline != "" %}
            <div class="homework-date">
                <span class="material-symbols-outlined">calendar_month</span>
                {{ this_week.last_homework.deadline }}
            </div>
            {% endif %}

            {% if this_week.last_homework.link != "" %}
            <a class="label label-red" href="{{this_week.last_homework.link}}">
                <span class="material-symbols-outlined">description</span>Handout
            </a>
            {% endif %}
        {% else %}
            None for this week!
        {% endif %}
    </div>

    <div class="header">
        Upcoming Assignments
    </div>
    <div class="content">
        {% if this_week.next_homework %}
            <div class="homework-name">
                {{ this_week.next_homework.name }}
            </div>

            <div class="homework-date">
                <span class="material-symbols-outlined">calendar_month</span>
                Released {{ this_week.next_homework.date }}
            </div>

            {% if this_week.next_homework.deadline != "" %}
            <div class="homework-date">
                <span class="material-symbols-outlined">calendar_month</span>
                {{ this_week.next_homework.deadline }}
            </div>
            {% endif %}

            {% if this_week.next_homework.link != "" %}
            <a class="label label-red" href="{{this_week.next_homework.link}}">
                <span class="material-symbols-outlined">description</span>Handout
            </a>
            {% endif %}
        {% else %}
            None!
        {% endif %}
    </div>

</div>

</div>

## Important Links

<div id="important-links">

{%- set links = extra.links -%}

{% for link in links %}
<a class="card" href="{{link.link}}" target="_blank">
<div class="content">
<img class="icon" src="{{link.icon}}" alt="{{link.name}} icon">
</div>
<div class="name">
{{ link.name }}
</div>
</a>
{% endfor %}

</div>

## Office Hours Calendar
<iframe id="class-calendar" src="https://calendar.google.com/calendar/embed?height=600&wkst=1&ctz=America%2FNew_York&showPrint=0&mode=MONTH&src=Y185Y2EyMWY0NThhNTlmMDhkNDc1ZWFlNjU4ODNkODRiYzBiM2E3ZjMwNDgxYzNlZWFjMzE3NmVkN2ZmNTQzZmFiQGdyb3VwLmNhbGVuZGFyLmdvb2dsZS5jb20&color=%23f6bf26" style="border-width:0" width="800" height="600" frameborder="0" scrolling="no"></iframe>

## Weekly Schedule

<div id="schedule" markdown>

<!-- Loading in schedule from schedule.yaml -->

{%- set schedule = extra.schedule -%}

{% if schedule %}
{% set ns = namespace(recitation_days_left=0, homework_days_left=0) %}

<table>
    <thead>
        <th><b>Date</b></th>
        <th><b>Class</b></th>
        <th><b>Reading</b></th>
        <th><b>Homework</b></th>
    </thead>
    <tbody>
        {% for schedule_day in schedule %}
        <tr>
            <td><span class="schedule-day">{{schedule_day.date}}</span></td>

            <td><span class="schedule-lecture">
                {% if schedule_day.lecture.name != ""  %}
                    {% if schedule_day.lecture.link != "" %}
                        <a class="label label-gold" href="{{schedule_day.lecture.link}}" target="_blank">
                            {{schedule_day.lecture.name}}
                        </a>
                    {% else %}
                        <b>{{schedule_day.lecture.name}}</b>
                    {% endif %}
                {% endif %}
            </span></td>

            <td><span class="schedule-reading">
                {% if schedule_day.reading.name != "" %}
                    <a class="label label-blue" href="{{schedule_day.reading.link}}" target="_blank">
                        {{schedule_day.reading.name}}
                    </a>
                {% endif %}
                {% if schedule_day.reading.name2 %}
                    {% if schedule_day.reading.name2 != "" %}
                        <a class="label label-blue" href="{{schedule_day.reading.link2}}" target="_blank">
                            {{schedule_day.reading.name2}}
                        </a>
                    {% endif %}
                {% endif %}


            </span></td>

            {% if schedule_day.homework.name != "" %}
                <td rowspan="{{schedule_day.homework.numDays}}"><span class="schedule-homework">
                    <b>{{schedule_day.homework.name}}</b>
                    <br/>
                    {{schedule_day.homework.deadline}}
                    <br/>

                    {% if schedule_day.homework.link != "" %}
                    <a class="label label-red" href="{{schedule_day.homework.link}}">
                        <span class="material-symbols-outlined">description</span>Instructions
                    </a>
                    {% endif %}
                </span></td>
                {% set ns.homework_days_left = schedule_day.homework.numDays - 1 %}
            {% else %}
                {% if ns.homework_days_left > 0 %}
                    {% set ns.homework_days_left = ns.homework_days_left - 1 %}
                {% else %}
                    <td><span class="schedule-homework"></span></td>
                {% endif %}
            {% endif %}
        </tr>
        {% endfor %}
    </tbody>

</table>

{% else %}
Coming Soon!
{% endif %}

</div>

## Staff

### Instructors

<div id="course-instructors">
{%- set instructors = extra.staff | selectattr("role", "==", "Instructor") | list -%}
{% for instructor in instructors %}
<div class="staffer card">
    <div class="container">
        <img class="staffer-image" src="/assets/images/{{instructor.photo}}" alt="">
        <div>
            <h3 class="staffer-name">
                {{instructor.name}}
            </h3>
            <div class="staffer-links">
                <a href="mailto:{{instructor.email}}"><span class="material-symbols-outlined">
                    mail
                </span></a>
                {% if instructor.website %}
                <a href="{{instructor.website}}" target="_blank"><span class="material-symbols-outlined">
                    public
                </span></a>
                {% endif %}
            </div>
        </div>
    </div>
</div>
{% endfor %}

</div>

{%- set assistants = extra.staff | selectattr("role", "==", "Teaching Assistant") | list -%}
{%- set num_teaching_assistants = assistants | count -%}

{% if num_teaching_assistants > 0 %}

### Teaching Assistants

<div id="course-assistants">

{% for assistant in assistants %}

<div class="staffer card">
    <div class="container">
        <img class="staffer-image" src="/assets/images/{{assistant.photo}}" alt="">
        <div>
            <h3 class="staffer-name">
                {{assistant.name}}
            </h3>
            <div class="staffer-links">
                <a href="mailto:{{assistant.email}}"><span class="material-symbols-outlined">
                    mail
                </span></a>
                {% if assistant.website %}
                <a href="{{assistant.website}}" target="_blank"><span class="material-symbols-outlined">
                    public
                </span></a>
                {% endif %}
            </div>
        </div>
    </div>
</div>
{% endfor %}

</div>
{% endif %}
