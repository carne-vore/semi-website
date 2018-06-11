---
bodyclass: page--knowledge-base knowledge-flow-start
layout: article-overview-new
show-topic: Getting started with SeMI
page-heading: I love to get started with SeMI, tell me more!
section-intro-text: If you are new to SeMI, read these articles first to understand why SeMI is valuable for your organization.
---

<!-- THIS PAGE CONTAINS THE INDEX FOR THIS FOLDER -->

<div class="article-container">
    {% assign items_grouped = site.pages | group_by: 'topic' | sort: 'topic' %}
    <dl class="article-toc">
        {% for group in items_grouped %}
            <dt data-group="{{ group.name }}">{{ group.name }}</dt>
            <dd>
                <ol class="list-ordered">
                    {% for page in site.pages %}
                        {% if page.topic == group.name %}
                            <li><a href="{{ page.url }}">{{ page.date | date: '%B %d, %Y' }}{{ page.title }}</a></li>
                        {% endif %}
                    {% endfor %}
                </ol>
            </dd>
        {% endfor %}
    </dl>
    
    <section>
        <!-- Breadcrumbs for overview-->
		<ol class="breadcrumb">
			<li><a href="/knowledge-base">Knowledge base</a></li>
			<li>{{ page.show-topic }}</li>
		</ol>
        <h1>{{ page.show-topic }}</h1>
        <p>{{ page.section-intro-text }}</p>
        <ul class="article-overview">
            <section>
                <li>
                    {% for subpage in site.pages %}
                        {% if subpage.topic == page.show-topic %}
                            <ol>
                                <li><h3><a href="{{ subpage.url }}">{{ subpage.date | date: '%B %d, %Y' }} {{ subpage.title }}</a></h3>
                                    <p>
                                        {{ subpage.description }}
                                    </p>
                                    <dl class="tags">
                                        <dt><i>Tags</i></dt>
                                        <dd>
                                            <ul class="tags">
                                    			{% for tag in subpage.tags %}
                                					<li>{{ tag }}</li>
                                				{% endfor %}
                                			</ul>
                                        </dd>
                                    </dl>
                                </li>
                            </ol>
                        {% endif %}
                    {% endfor %}
                </li>
            </section>
        </ul>
    </section>
</div>